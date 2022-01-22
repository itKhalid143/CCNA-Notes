# Hacking Networks

Yersinia is a hacking framework package used for attacking layer2 devices

Notes:
	- Don't use default configurations, shutdown ports that aren't in use / putting them in seperate VLAN. 
	Man In the Middle
		- DHCP Snooping, How DHCP attack works: DHCP rogue server attack
				- We exhaust the DHCP pool using Yersiniya (Filling up every free spot, so the new users can't have an IP), then creating a fake DHCP server.
				- Fix: (Commands on the switch)
					- ip dhcp snooping, ip dhcp snooping vlan 1 (Dropping every DHCP port)
					- Enabling a trusted port (Router), int g0/0, ip dhcp snooping trust
					- Limiting DHCP requests from other untrusted ports to avoid DDOS and traffic attacks, int g0/2, ip dhcp snooping limit rate 10.
					- no ip dhcp snooping information option (To search for)
		- ARP poisoning
			- Fix:
				- Dynamic ARP Inspection
		- Forwarding requests from Kali to the Internet, sysctl -w net.ipv4.ip_forward=1 
		- aireplay --check wlan0 (to check whether the wireless card support the injections)