# Managing Cisco Devices

# Cisco Router has multiple Components:

- Central Porcessing Unit CPU: Execute operating instructions
			- System Initialization.
			- Routing functions.
			- Switching functions.
	
	- Interfaces (Srial, Fast, Gigabit)
	
	- Read Access Memory RAM
			- Volatile memory, contains data structures and softwares memory.
			- Copies the entire Cisco IOS software into RAM during the boot Process.
			- Running Configuration is stored on the RAM, Commands that are Configured on the router (show run).
	
	- Read Only ROM
			- Contains microcode for basic functions to start and maintain the router.
			- ROM Monitor, Password recovery (Router Disaster Recovery Functions)
			- Storing IP Routing Tables.
			- ARP Cache.
	
	- Flash memory
			- NonVolatile Computer memory.
			- Permanent Storage for the Operating System.
			- Similar to HDD/Flash Drive.
	
	- NVRAM
			- Non Volatile Ram, wr Command saved on NVRAM. (start-up configuration)
			- To permemntaly store the changes.
			- Configuration register, to control how a router boots.
	
After booting Up:
				- OS copied from the Flash memory to the RAM, and the runs from the RAM.

Packet Buffers:
				- Stored When packets are recieved on interfaces.
	
## Cisco Interfaces:

- Auxiliary Port - Modem CONNECTIONS
- Consol Port
- USB Interace
- Serial Interfaces
- FastEthernet Interfaces
- Gigabit Interfaces
- PVDM : Voice Environement
- DSP Digital Signal Processor

## Power on Self Test: _POST_
	
- Testing the basic functionality of the router hardware, Working, Supported, which components are present.

## Booting Steps:

- Perform POST
- Loads and runs bootstrap code
	- Loads the images into RAM, and starts the IOS
- Find the Cisco IOS software
	From configreg, IOS in flash, in TFTP server, ROM monitor
- Startup config in NVRAM

Configuration register/File
	- Determine where Cisco IOS files, which file to use.
	- Boot into ROM minitor mode if no Cisco IOS is available


## ROM Monitor:
	
- Low level Operating System (Password recovery, Testing, TroubleShooting)

## Cisco IOS

- Cisco IOS Integrated File system
		Navigate
		Manipulate directories on a Cisco devi

- File system
		Flash memory
		Network file Systems

## IOS Naming Conventions

C2900	-	Universal k9			-			mz.						SPA-												152-4.MA			.bin			
Platform 	Feature set-universal(IP base, Security, etc)		File Format-m (runs in RAM), z (Compressed)	Digitally Signed Software Image (P Production Image, S - Special Image, A - Key version)	Software version Number		Fine Extention, binary executable	


## Commands:

	sh version
	sh run (Current Configuration)
	sh flash
	sh start (Startup Configuration)

## Configuration register (Hex number) 16-bit

Example: config-register 0x2100 (booting up to rommon) (2102 Normal BOOT)
			https://www.cisco.com/c/en/us/support/docs/routers/10000-series-routers/50421-config-register-use.html

## Backups and Upgrading

Backup		-	copy flash: tftp:
		copy flash running-config

Upgrade
		copy tftp: flash:
		boot system flash:

TFTP
	- (Overwritting)	When copying Start config from the tftp, it overwrite the current running config in the router!
	- (Merge) 	When copying Running config from the tftp, it does not overwrite the current running config, it does only in the conflict state, there were many configs.

	To choose the IOS from the flash, boot system flash IOSName

## Password Recovery

https://www.cisco.com/c/en/us/support/docs/routers/2800-series-integrated-services-routers/112033-c2900-password-recovery-00.html

- Router Recovery:	https://www.cisco.com/c/en/us/td/docs/routers/access/4400/troubleshooting/guide/isr4400trbl/isr4400trbl02.html

- Switch Recovery:	https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst3560/software/release/12-2_52_se/configuration/guide/3560scg/swtrbl.html#wp1021182