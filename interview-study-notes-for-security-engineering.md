# Security Engineering at Google: My Interview Study Notes
## By [nolang](https://twitter.com/__nolang)

### Contents
- [README](README.md)
- [Networking](#networking)
- [Web application](#web-application)
- [Infrastructure (Prod / Cloud) Virtualisation](#infrastructure-prod--cloud-virtualisation)
- [OS implementation and systems](#os-implementation-and-systems)
- [Mitigations](#mitigations)
- [Cryptography, authentication, identity](#cryptography-authentication-identity)
- [Malware & Reversing](#malware--reversing)
- [Exploits](#exploits)
- [Detection](#detection)
- [Digital Forensics](#digital-forensics)
- [Incident Management](#incident-management)
- [Coding & algorithms](#coding--algorithms)
- [Security themed coding challenges](#security-themed-coding-challenges)
- [Learning tips](#learning-tips)
- [Interviewing tips](#interviewing-tips)

# Web application 

- Same origin policy
	- Only accept requests from the same origin domain. 
 
- CORS 
	- Cross-Origin Resource Sharing. Can specify allowed origins in HTTP headers. Sends a preflight request with options set asking if the server approves, and if the server approves, then the actual request is sent (eg. should client send auth cookies).

- HSTS 
	- Policies, eg what websites use HTTPS.

- Cert transparency 
	- Can verify certificates against public logs 
	
- HTTP Public Key Pinning
	- (HPKP)
	- Deprecated by Google Chrome

- Cookies 
	- httponly - cannot be accessed by javascript.

- CSRF
	- Cross-Site Request Forgery.
	- Cookies.

- XSS
	- Reflected XSS.
	- Persistent XSS.
	- DOM based /client-side XSS.
	- `<img scr=””>` will often load content from other websites, making a cross-origin HTTP request. 

- SQLi 
	- (Wo)man in the browser (flash / java applets) (malware).
	- Validation / sanitisation of webforms.

- POST 
	- Form data. 

- GET 
	- Queries. 
	- Visible from URL.

- Directory traversal 
	- Find directories on the server you’re not meant to be able to see.
	- There are tools that do this.

- APIs 
	- Think about what information they return. 
	- And what can be sent.

- Beefhook
	- Get info about Chrome extensions.

- User agents
	- Is this a legitimate browser? Or a botnet?

- Browser extension take-overs
	- Miners, cred stealers, adware.

- Local file inclusion
- Remote file inclusion (not as common these days)

- SSRF 
	- Server Side Request Forgery.

- Web vuln scanners. 
- SQLmap.
- Malicious redirects.


# Infrastructure (Prod / Cloud) Virtualisation 

- Hypervisors.
- Hyperjacking.
- Containers.
- Escaping and privilege escalation techniques.
- Site isolation.
- Network connections from VMs / containers. 
- Side-channel attacks. 
- Beyondcorp 
	- Trusting the host but not the network.

# Malware & Reversing

- Interesting malware
	- Conficker.
	- Morris worm.
	- Zeus malware.
	- Stuxnet.
	- Wannacry.
	- CookieMiner.
	- Sunburst.

- Malware features
	- Various methods of getting remote code execution. 
	- Domain-flux.
	- Fast-Flux.
	- Covert C2 channels.
	- Evasion techniques (e.g. anti-sandbox).
	- Process hollowing. 
	- Mutexes.
	- Multi-vector and polymorphic attacks.
	- RAT (remote access trojan) features.

- Decompiling/ reversing 
	- Obfuscation of code, unique strings (you can use for identifying code).
	- IdaPro, Ghidra.

- Static / dynamic analysis
	- Describe the differences.
	- Virus total. 
	- Reverse.it. 
	- Hybrid Analysis.

# Exploits

- Three ways to attack - Social, Physical, Network 
	- **Social**
		- Ask the person for access, phishing. 
		- Cognitive biases - look at how these are exploited.
		- Spear phishing.
		- Water holing.
		- Baiting (dropping CDs or USB drivers and hoping people use them).
		- Tailgating.
	- **Physical** 
		- Get hard drive access, will it be encrypted? 
		- Boot from linux. 
		- Brute force password.
		- Keyloggers.
		- Frequency jamming (bluetooth/wifi).
		- Covert listening devices.
		- Hidden cameras.
		- Disk encryption. 
		- Trusted Platform Module.
		- Spying via unintentional radio or electrical signals, sounds, and vibrations (TEMPEST - NSA).
	- **Network** 
		- Nmap.
		- Find CVEs for any services running.
		- Interception attacks.
		- Getting unsecured info over the network.

- Exploit Kits and drive-by download attacks

- Remote Control
	- Remote code execution and privilege.
	- Bind shell (opens port and waits for attacker).
	- Reverse shell (connects to port on attackers C2 server).

- Spoofing
	- Email spoofing.
	- IP address spoofing.
	- MAC spoofing.
	- Biometric spoofing.
	- ARP spoofing.

- Tools
	- Metasploit.
	- ExploitDB.
	- Shodan - Google but for devices/servers connected to the internet.
	- Google the version number of anything to look for exploits.
	- Hak5 tools.

- Look at mitre attack matrix
	- https://attack.mitre.org/

# Digital Forensics

 - Evidence volatility (network vs memory vs disk)

 - Network forensics
	- DNS logs / passive DNS
	- Netflow
	- Sampling rate

 - Disk forensics
	- Disk imaging
	- Filesystems (NTFS / ext2/3/4 / AFPS)
	- Logs (Windows event logs, Unix system logs, application logs)
	- Data recovery (carving)
	- Tools
	- plaso / log2timeline
	- FTK imager
	- encase

 - Memory forensics
	- Memory acquisition (footprint, smear, hiberfiles)
	- Virtual vs physical memory
	- Life of an executable
	- Memory structures
	- Kernel space vs user space
	- Tools
	- Volatility
	- Google Rapid Response (GRR) / Rekall
	- WinDbg

  - Mobile forensics
	- Jailbreaking devices, implications
	- Differences between mobile and computer forensics
	- Android vs. iPhone

  - Anti forensics
	- How does malware try to hide?
	- Timestomping

  - Chain of custody
  	- Handover notes 

# Incident Management

- Privacy incidents vs information security incidents
- Know when to talk to legal, users, managers, directors.
- Run a scenario from A to Z, how would you ...

- Good practices for running incidents 
	- How to delegate.
	- Who does what role.
	- How is communication managed + methods of communication.
	- When to stop an attack.
	- Understand risk of alerting attacker.
	- Ways an attacker may clean up / hide their attack.
	- When / how to inform upper management (manage expectations).
	- Metrics to assign Priorities (e.g. what needs to happen until you increase the prio for a case)
    - Use playbooks if available

- Important things to know and understand
	- Type of alerts, how these are triggered.
	- Finding the root cause.
	- Understand stages of an attack (e.g. cyber-killchain)
	- Symptom vs Cause.
	- First principles vs in depth systems knowledge (why both are good).
	- Building timeline of events.
	- Understand why you should assume good intent, and how to work with people rather than against them.
    - Prevent future incidents with the same root cause

  - Response models
  	- SANS' PICERL (Preparation, Identification, Containement, Eradication, Recovery, Lessons learned)
   	- Google's IMAG (Incident Management At Google)

# Coding & algorithms

- The basics
	- Conditions (if, else).
	- Loops (for loops, while loops).
 	- Dictionaries.
 	- Slices/lists/arrays.
 	- String/array operations (split, contaings, length, regular expressions).
 	- Pseudo code (concisely describing your approach to a problem).

- Data structures
	- Dictionaries / hash tables (array of linked lists, or sometimes a BST).
	- Arrays.
	- Stacks.
	- SQL/tables. 
	- Bigtables.

- Sorting
	- Quicksort, merge sort.

- Searching 
	- Binary vs linear.

- Big O 
	- For space and time.

- Regular expressions
	- O(n), but O(n!) when matching.
	- It's useful to be familiar with basic regex syntax, too.

- Recursion 
	- And why it is rarely used.

- Python
	- List comprehensions and generators [ x for x in range() ].
	- Iterators and generators.
	- Slicing [start:stop:step].
	- Regular expressions.
	- Types (dynamic types), data structures.
	- Pros and cons of Python vs C, Java, etc.
	- Understand common functions very well, be comfortable in the language.

## Security themed coding challenges

- Cyphers / encryption algorithms 
	- Be able to implement basic cyphers.

- Parse arbitrary logs 
	- Practice text parsing.

- Web scrapers 
	- Another way to practice text parsing.

- Port scanners 
	- Practice parsing network information.

- Botnets
	- How would you build ssh botnet.

- Password bruteforcer
- Scrape meta data from PDFs 
- Script to recover deleted items
- A program that looks for malware signatures in binaries / code samples

# Learning tips 

- [Learning How To Learn course on Coursera](https://www.coursera.org/learn/learning-how-to-learn) is amazing and very useful. Take the full course, or read [this summary on Medium](https://medium.com/learn-love-code/learnings-from-learning-how-to-learn-19d149920dc4).

- **Track concepts - "To learn", "Revising", "Done"**
	- Any terms I couldn't easily explain went on to post-its. 
	- One term per post-it. 
	- "To learn", "Revising", "Done" was written on my whiteboard and I moved my post-its between these categories, I attended to this every few days.
	- I looked up terms everyday, and I practiced recalling terms and explaining them to myself every time I remembered I had these interviews coming up (frequently).
	- I carried around a notebook and wrote down terms and explanations. 

- **Target your learning**
	- Think *hard* about what specific team you are going for, what skills do they want? If you aren't sure, then ask someone who will definitely know.

- **Identify your weaknesses.** 
	- If you're weak on coding and you find yourself avoiding it, then spend most of your study time doing that.

- **Read**
	- Read relevant books (you don't have to read back to back).
	- When looking up things online, avoid going more than two referral links deep - this will save you from browser tab hell.

- **Mental health**
	- Take care of your basic needs first - sleep, eat well, drink water, gentle exercise. You know yourself, so do what's best for you.
	- You are more than your economic output, remember to separate your self worth from your paycheque. 
	- See interviews for what they are - they are *not* a measure of you being "good enough".

# Interviewing tips 

- **Ask questions**
	- Questions create thirst for answers.
	- Ask questions to yourself when you’re studying, to the people you are studying with.
	- Questions reveal how you approach problems.
	- Ask your interviewer lots of questions. They often intentionally ask questions with few details.

- **Say what you are thinking**
	- The interviewer can only make an evaluation on your suitability for the job based on the things you *say*. 
	- If you don't say your thought process aloud, then the interviewer doesn't know what you know. 
	- Practice saying everything you know about a topic, even details you think might be irrelevant. 
	- Write pseudo code for your coding solution so you don't have to hold everything in your head.

- **Reduce cognitive load**
	- If the infrastructure is complicated, draw up what you think it looks like. 
	- Write tests and expected output for code you write, test your code against it. 
	- Take notes about the questions so you don't forget important details.

- **Prepare**
	- Prepare questions that you want to ask your interviewers so you don't need to think of them on the spot on the day. Since an interview is also for you to know more about the workplace, I asked questions about the worst part of the job. 
	- Bring some small snacks in a box or container that isn't noisy and distracting. A little bit of sugar throughout the day can help your problem solving abilities. 
	- Stay hydrated - and take a toilet break between every interview if you need to. 

- **Do practice interviews**
	- Do them until it's comfortable and you can easily talk through problems
	- Ask them to give you really hard questions that you definitely don't know how to answer
	- Practice being in the uncomfortable position where you have no idea about the topic you've been asked. Work through it from first principles.
	- Doooo theeeeemmm yes they can be annoying to organise but it is *worth it*.

### Interviewers are potential friends and they want to help you get the job, they are on your side. Let them help you, ask them questions, say everything you know on a topic and *say your thought process out loud*.
