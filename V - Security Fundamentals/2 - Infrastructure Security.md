# Infrastructure Security

## Enable

- Password (Not Recommended)
		- Saved in clair texts by default.
		- service password-encryption (To enable encryption, Type-7, Not secured at all)
		- to Decrypt use thise link, http://learnccna.net/cisco-type-7-password-decryption-2/73D9CD6E4B859E7B0978A7378A959B6890EF0DE9A93FA5122B6B10F5ED5122C8CD0583C3AA79253EBC64724A2B2655E3/

- Secret (Recommended)
		- MD5 hashing, Encrypted by default.
		- Hashings, http://learnccna.net/hashing/40F5D3C02039392E01C88E12B34105253F2E6FBF20C0890D025449261ECA49B1A9631A3012F72462EBBF899129904BD3/

You can lock out of router (CCNP)

## Disable

Unused Services (DNS, CDP, Tcp-small, HTTP, Telnet, etc.)

## Line Console Security

- Console line (line con 0, password, login), local (asking for Username and Password)
				- login, means it's required rather than the normal password/secret
				- exec-timeout (0 0 - default), it will timeout if we went idle in the CLI.
				- username <name> <0-15> priviledge level password/secret <password>
				- logging synchronous, it will automatically retyped at debugging level.

- line aux 0
			- line vty 0 <0-x>
				- Telnet, 0-X simultaneously connections.
				- login, (Password is required), local
				- password <pwd>
				- exec-timeout, When there's no activity
				- transport input telnet/ssh (Change Transport input)

- SSH
		- In order to enable SSH, we change the device hostname, enable ip domain-name, have to have a username/password, and generate keys,  crypto key generate rsa modulus (The larger, the more secure)
		- ip ssh version 2 (More secure)

## Banner - Display a message before accessing the device
	
- Message of the day Banner (Temporary message)
		- Displayed on all the lines. 
- Login banner (Before the user login)
- Exec (After successful login)


`Commands:
		- To check open ports on the router: 
				- show control-plane host open-ports
		- show users
		- show line (* active), clear line <number>, to disconnect a session
		- (incase of vty) ctrl+shift+6 (make a session), show sessions, disconnect.`
