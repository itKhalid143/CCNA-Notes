# Types of Network Management Protocols:
	
How they work:

## Query-based

- Send requests and ask.

- Advantanges:
	- Reliable, No response equals to a Problem, can be Sheduled (for every xTemp).

## Event-Based
	
- Listen for annoucements/Logs. (ex, Interface went down)
	- NMS (Network Management System) listens based: Syslogs, SNMP Traps, Debugging (Enabled).
	- Not reliable.
		- Advantages:
			- React very quickly on that event, rather than waiting for the shedule.

We should use Both for the Network Managements, we have to make meaningful Decisions
- Alerts and Reports. (*notify when happens, *detail of Performance)*

## Network Management Planning (Before Implementing):
	
- Translating business requirements (Monitoring needs, thresholds(level that the limit shouldn't go up to), Network Performance Monitor).
- Building and levaraging reports.
- Determining and Monitoring (Scopes and Impacts).
- Data retention.
- Availability. (Down time)
- Performance and Capacity planning.
- Polling Frequency.
- Impact of Netowrk Toplogy.
- Distributed Network Management Architecture (Multiple Data center, Multiple copies of NPM)
- Pay attention when traffic is allowed and when is denied (Making a separate management VLAN for SNMP) to make CLs and Firewall rules.
	- Different Security Zones.

***

# SNMP : Network Management Protocols
	
## Types:
	- ICMP/Ping (Availability calculations, Latency response timers).
	- SNMP : Query a device (State of the device) (Used in all Statistics).
	- WMI (Windows Management Instrumentation) to check for performance counter types value (So Slow).

## SNMP: Simple Network Managemnt Protocol
	
- Get/Post requests Contains OID Values.

Key Words to remember:

- MIBs: Management Information Base (RFC 1213)
		- Larder Entity, Management information bases.
		- Database use for managing entities in a network (Ex, SNMP) (Tree structure)
		- Contains Groups (Variables depends on the manufactura)

- OIDs:
		- Object Identifiers, included within a MIB.
		- Use for polling a specific interface. (Acts as a Bean in the network)
		- Numbers that can be replaced by the value of the request.
			- 1.3.6.1.2.2.2.1.2 = Interface Description as Exaxmple
- Performance Counters:
		- Network Management Applications.

## TroubleShooting:

- Syslog Protocol (Must check RC-5424):
	- show logging, logging levels (Severity)

## Notes:

- Some firewalls block ICMP requests with 0 payloads or huge payloads, NPM sends/recieves ICMP requests with Data.
- SNMP uses UDP:161.
- Make sure that firewalls/ACLs allows SNMP protocol.

***

# Syslog Protocol (Must check RC-5424):

- show logging, logging levels (Severity 0-7 ) 
	- (If 7 is enabled 0-6 all automatically enabled)
        		      	0       Emergency: system is unusable
              			1       Alert: action must be taken immediately
              			2       Critical: critical conditions
              			3       Error: error conditions
              			4       Warning: warning conditions
              			5       Notice: normal but significant condition
              			6       Informational: informational messages
              			7       Debug: debug-level messages
	- ip logging synchronous, text is recopied after a logging message appears
	- Must enable timestamps, inorder for the syslog to be timed.
		
## Syslogs Discriminator:
	
- Console logging
		- logging console <severity>
		- Appears on the console when doing a move.
- Monitor logging
		- syslogs in the console but nothing in the telnet session (Terminal), to fix that:
		- We sohuld enable terminal monitor. (terminal monitor)
- Buffer logging
		- We're seeing the logggin in the buffer, plus the size of that buffer.
		- show log | include BDR <To see the buffer syslog saved messages>
		- The logging messages saved on the buffers, we can get them back whenever we want, we save them rather than they show automatically wether on the console or in the vty.
