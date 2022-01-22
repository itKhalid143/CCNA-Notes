# Port Security

Port Security looks at the source MAC Address of frames received on a port, we can restrict those frames to a single MAC Adress / Limited Mac Address.
	Learning:
		- Static Learning
		- Dynamic Learning
		- Static & Dynamic Learning
		- Sticky Learning

## Commands
			- show port security
			- switchport mode access
			- int x/x/x, switchport port-security (Maximum allowed 1 by Default) (The first host that is connected, is permitted, Secure Dynamic as Default)
			- switchport port-security maximum X 		(Maximum MACs)
			- switchport port-security mac-address X	 (Static MAC)
								- sticky (When MAC is dicovered, it will automatically add it to the configuration, dynamic learning and statically saved, it will be removed after the reload)
			- switchport port-security 	 (Vaiolation MAC)
				- Protect, means dropping packets with unknown sources
				- Restrict
				- Shutdown
			- show interface status
			- When there is a vaiolation, errdisable recovery interval 30 (It will self recover from the shutdown)