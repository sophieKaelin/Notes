# OS implementation and systems

- Privilege escalation techniques, and prevention. ✅
	- Look for programs running as root and inject
	- sudo into privledges 
- Buffer Overflows. ✅
	- Overwriting into adjacent memory. If you know what's there, you can overwrite on purpose. 
- Directory traversal (prevention). ✅
	- validate and sanitise user input. Avoid passing user input into to file system APIs if possible. 
- Remote Code Execution / getting shells. ✅
	- Look for command injection, send a script that will run on victim machine to create a shell on another computer. Use netcat to listen. 

- Windows ✅
	- Windows registry and group policy. 
		- Stores information about software, hardware, user preferances, os configs.
		- How I fixed HDMI on my laptop
		- Group policy mandated by management for a group, windows registry is for personal user. Group policy influences registry.
	- Windows SMB. 
		- Server Message Block
		- File sharing between hosts on a network (1.0 is vulnerable, wannacry)
	- Samba (with SMB).
		- Connection between OS (Linux to Windows) (or any unix based system really)
		- reimplementation of SMB	
	- Buffer Overflows. 
	- ROP. ❌ (still unsure how this works(
		- Return oriented Programming
		- Like stack smashing -> defence, make it non-executable
		- Exploit even with defences in place
		- Use existing code to return to something else

- Unix ✅
	- SELinux.
		- Security Enhanced Linux
		- Security Architecture for linux systems
		- Admin have more say in access control
		- AVC (Access Vector Cache) contains cached permissions for subjects/objects (software/files)	
	- Kernel, userspace, permissions.
		- Memory is divided into 2 spaces Kernal and User space
		- Userspace: memory location for all user activity
		- Kernal has access to all memory, userspace only has access to a portion
		- provides memory protection
		- Permissions: read, write and execute. CHMOD allocates permissions. 
	- MAC vs DAC.
		- Mandatory vs Discretionary
		- Mandatory is military grade. Root user determines privledges of all files.
		- Discretionary is up to the file owner to assign privleges. Less secure but more user friendly. 
	- /proc
		- contains runtime system information (not REAL information)
		- interface to kernel data structures
		- Ways of getting kernel information for userspace
	- /tmp - code can be saved here and executed.
		- Saved here before shutting down.
		- Backups might be saved here?
		- Often important files for programs running at that time.
	- /shadow 
		- Stores actual encrypted passwords
		- only readable by root
	- LDAP 
		- Lightweight Directory Browsing Protocol
		- Lets users have one password for many services
		- Similar to Active Directory in windows.
		- Can run multiple instances, rather than just the one.
		- Allows communicatation between other directory servers (LDAP is a way of speaking to AD)

- MacOS
	- Gotofail error (SSL).
		- Vuln ~2016
		- When accessing HTTPS resources using SSL on Iphone, bug in the code where "GoTo Fail" is accidentally written twice. Regardless of result of condition, the second one is always executed.
		- Skips vital verification steps in ensure a secure connection with SSL
	- MacSweeper. ❌ (need to read up more on this)
		- "scans for vulnerabilities and reports" -> these reports are exaggerated/fake
		- Just a big scam 
	- Research Mac vulnerabilities.

- Local databases
	- Some messaging apps use sqlite for storing messages.
	- Useful for digital forensics, especially on phones.

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
