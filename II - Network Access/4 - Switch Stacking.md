# Switch Stacking

![Stacking](/II%20-%20Network%20Access/Screenshots/stacking.png)


Switch Stacking, Connecting 2 or more switchs in a specific way with specific cables:
	- they appear to be a single switch. (Configured and seen as Single)
	- CDP, STP, VTP see them as a single S.

## Advantages:
	
- Manage the stack with a single IP .
- Telnet / SSH to one Switch.
- One Configuration File.
- STP, CDP, VTP are running on one Switch.
- The ports on each physical switches appear to be part of the same logical switch
	- One Mac Table.
	- Provide Redundancy.

Different technologies, 
	Cicso FlexStack (2960 Switches)
	Flexstack plus	(3750 Switchs support Stack wise)

**Master Switch** controls the Stack, Forward the requests, Match the frame to Mac table and decide.
			
**Switch Stacking** : Used in Access Layer

We have to buy the right Products in order to make the stacking work. (Year introduced 2010+)

**Models supported**, 
	Flex Stack	2010, 2960-S X	, 10Gbps, 4 Switches Maximum
	FlexStack Plus	2013, 2960-X XR	, 20Gbps, 8 Switches Maximum	

	
## Chassis Aggregation:

Used in Distribution and Core layers of a Network.
	- Higher-end switches, two Switches, Complex, the same as switch Stacking.
	- High availability design.

Activate using
	Multichassis ether channel
