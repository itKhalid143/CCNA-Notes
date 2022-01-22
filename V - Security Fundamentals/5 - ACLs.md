# Access Control List

ACLs: is sequential list of statements and the router will check from the first line to the last until it gets a match, if not it will be dropped.
	Purpose
		- Permitting / Denying Traffic in Interfaces.
	Applications
		- Classifications
			- Used in IPsec
			- Used in Routing
			- Used in NAT, etc.
	Inbound / Outbound
			- Applied Inbound on an interface, ACL processed before being routed.
	Creations Steps:
		- Create ACL in global configuration,  access-list command
		- Apply inbound / Outbound on an interface, access-group command

***
# Types of ACLs

Types of ACLs:
			- Standard ACL
					- Only check on source Adresses, permits or denies the entire protocol suite based on source Network.
			- Extended ACL
					- Check on Source and Destination, permits and denies based on ports and applications.
		To determine the Type we use: 
				- Numbered ACLs
						- 1-99 / 1300-1999 	used for Standard ACLs
						- 100-199 / 2000-2699	used for Extended ACLs
						- Number range specifies protocol (IP/IPX/APPLEtalek, etc)
				- Named ACLs
						- Alphanumeric characters, more descriptive.

***
## Wildcard Mask

Wildcard Mask (Inverse Mask)
		0 in mask, means a Match
		1 in mask, means a Ignore
			Examples: 10.1.1.1 0.0.0.0 (Match the same IP)
		permit anything

***

## Notes:

Notes:
		- It will follow the instructions from the first to the last, (It can cause problems if we permit any then on the second like we denied a host, it will be ignored)
		- Best Practice, Standard ACLs close to the destination as possible
		- Best Practice, Extended ACLs close to the Source as possible

## Commands: 
		Standard ACLs
			- access-list 10 permit HOST 
			- access-list 10 remark This access list for doing X 
			- int x/x/x
			- access-class 10 inbound
			- no access-list 10 
		Extended ACLs
			- access-list 100 permit <Application> <Source> <Destination> eq/othermaths <80>
			- If we want to remove the line rather than the entire list, ip access-list extended 102, no 30
 

***

## IPv6 ACLs

		- IPv6 and IPv4 are independent of each others, different headers.
			- Specific values unique (Flow Label, DSCP Value)
		- Only use Names ACLs
		- Best Practice, using Ingress ACLs (Monitor before Processing)
			- Arrives from Internet, Ingress/Inbound
			- Leaving the LAN, Process Outbound
		- Be careful when dealing with ICMPv (Everything based on It from Discovery to to other functionalities)
		- Uses the prefix length Number (The number of contigueous bits that will be matched for that IPV Address)
		- Commands
				- ipv6 traffic-filter aclx in