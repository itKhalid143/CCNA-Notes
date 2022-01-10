# NTP - Network Time Protocol

- Clock Synchronization, UDP 123, Timing is great for troubleshooting in the Network.
- NTP uses a hierarchical, semi-layered system of time resources.
	- Each level of this hierarchy ias termed a stratum and is assigned a number starting with zero at the top.
	- NTP master 0

## NTP Hierarchy

![NTP](/IV%20-%20IP%20Services/Screenshots/ntp.png)

***

- Things to remember
	- Clients adjust their time from what they hear from an NTP server.
	- NTP servers supply time to clients
	- NTP need Trusted Clock Source. (NTP server, Domain Controller, NTP master)
	- Stratum Level
		- The quality of the time source, the lower, the better.
		- Is a device that has atomic, GPS, Radio clock, the better reference for clocks.