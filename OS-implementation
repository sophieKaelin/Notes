# OS implementation and systems

- Privilege escalation techniques, and prevention.
- Buffer Overflows.
- Directory traversal (prevention).
- Remote Code Execution / getting shells.

- Local databases
	- Some messaging apps use sqlite for storing messages.
	- Useful for digital forensics, especially on phones.

- Windows
	- Windows registry and group policy. 
	- Windows SMB. 
	- Samba (with SMB).
	- Buffer Overflows. 
	- ROP. 

- *nix 
	- SELinux.
	- Kernel, userspace, permissions.
	- MAC vs DAC.
	- /proc
	- /tmp - code can be saved here and executed.
	- /shadow 
	- LDAP - Lightweight Directory Browsing Protocol. Lets users have one password for many services. This is similar to Active Directory in windows.

- MacOS
	- Gotofail error (SSL).
	- MacSweeper.
	- Research Mac vulnerabilities.

## Mitigations 
- Patching 
- Data Execution Prevention

- Address space layout randomisation
	- To make it harder for buffer overruns to execute privileged instructions at known addresses in memory.

- Principle of least privilege
	- Eg running Internet Explorer with the Administrator SID disabled in the process token. Reduces the ability of buffer overrun exploits to run as elevated user.

- Code signing
	- Requiring kernel mode code to be digitally signed.

- Compiler security features
	- Use of compilers that trap buffer overruns.

- Encryption
	- Of software and/or firmware components.

- Mandatory Access Controls
	- (MACs)
	- Operating systems with Mandatory Access Controls - eg. SELinux.

- "Insecure by exception"
	- When to allow people to do certain things for their job, and how to improve everything else. Don't try to "fix" security, just improve it by 99%.

- Do not blame the user
	- Security is about protecting people, we should build technology that people can trust, not constantly blame users. 
