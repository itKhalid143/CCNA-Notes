# Port Mirroring

Port Mirroring:
		- The ports have no visibility of traffics of other port once the MAC Address in the Switch is filled, unless we enable Span/port monitoring.
		- Commands:
			- monitor session<1-66 Span Session> source<interface/remote/vlan> both<sent/recieved> 
			- monitor session<id> destination interface <int>
			- show monitor
		- Ingress disabled Traffic, no longer learning MAC Addresses from the span mirror, nor allowing traffic to come from that port.
			- Cannot ping the Port span.
		- Options:
			- remote Span.
		- Dependencies and rules:
			- A span destination port can only be used with one span session at a time.
			- A span destination can also not be a span source port.
			- Span destination is not behaved as ethernet port.
			- Removing the Span:
				- No minotr session
			- Multiple Span source, can be used within a single span session
			- One span session, cannot mix interfaces and Vlan sources, can use any combination of directions
			- EtherChannel, can be used as a source port.
			- Trunks can also be used as Source ports.

***
			
# SolarWinds

SolarWinds is a great company for network engineer:
		- Helps to monitor the traffics, the performances, and the routes.
			- Monitor the traffic overall.
		- Applications to Manage the Network:
			- GNS3 for Network Simulation.
			- NetPath for Network Paths and Routes.
			- Network Performance Monitor
			- Kiwi syslog Server
			- Kiwi Cattools