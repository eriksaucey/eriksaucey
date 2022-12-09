Main components
	msfconsole - main command-line interface
	Modules - supporting modules such as exploits, scanners, payloads, etc
	Tools - Standalone tools that will help vulnerability research, assessment, or penetration testing. 
		msfvenom
		pattern_create
		pattern_offset
Recurring Concepts
	Exploit: a piece of code that uses a vuln. present on the target system.
	Vulnerability: A Design, coding, or logic flaw affecting the target system. Exploitation of vulnerability can result in disclosing confidential information or allow an attacker to execute code on target system
	Payload: Exploit will take advantage of a vulnerability. Payload is the code that will run on a target system.
		Interactive connection that allows you to type commands that will be executed on the target system.
		This interactive command line is called a shell
			# tree -L 1 payloads/
		3 different directories
			1. Singles - self contained payloads (add user, launch notepad.exe, etc) that do not need to download an additional component to run.
			2. Stagers - Responsible for setting up a connection channel between Metasploit and the target system. Useful when working with staged payloads. Staged payloads will first upload a stager on the target system then download the rest of the payload.
				1. Advantage is the initial size of the payload will be relatively small compared to the full payload sent at once.
			3. Stages - Downloaded by the stager. This will allow you to use larger sized payloads.
			To identify single or staged payloads:
				Single: generic/shell_reverse_tcp
				Staged: windows/x64/shell/reverse_tcp
		
Modules and Categories
	Auxiliary: any supporting module, such as scanners, crawlers, fuzzers
		# tree -L 1 auxiliary/
	Encoders: Allow you to encode the exploit and payload in the hope that a signature based antivirus solution may miss them.
		# tree -L 1 encoders/
	Evasion - While encoders will encode the payload, the should not be considered a diect attempt to evade antivirus
		Evasion modules will try that with more or less success
			# tree -L 2 evasion/
	Exploits
		# tree -L 1 exploits/
	NOPS - do nothing (No Operations)
		represented with 0x90
			CPU will do nothing for one cycle
			Used as a buffer to achieve consistant payload sizes
		