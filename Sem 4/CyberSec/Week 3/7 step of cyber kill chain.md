
1. Recon
2. Weaponisation
3. Delivery
4. Exploitation
5. Installation
6. Command control
7. Action and Objection

**why is it important to understand how Cyber Kill Chain works?**
- Help understand and protect against attacks
- assess your network and system security by identify missing security controls and closing certain security gaps
- Recognise intrusion attempts and intruders goals and objectives

# Reconnaissance

- Discovering and collecting info on the systems and victim

**OSINT**
- Collecting every piece of information about the target, such as:
	- company's size
	- email addresses
	- phone numbers
	- etc

https://osintframework.com/

**Email harvesting**
- Process of obtaining email addresses from public, paid, or free services
- can use for phishing attack
- attacker would use social media like linkedIn, Facebook Twitter and instagram
- the information can be used to conduct a phishing attack

# Weaponisation

- Combine malware and exploit to create a deliverable payload, 
- People usual use automated tools or just buy from darkweb

**In this phase attacker would:**
- Create an infected file or payload 
- Select backdoor implant

# Delivery

- When the attacker decide the method for delivery

**Phishing Email:**
- craft a specific email that would target a specific person or multiple person in the company
- Take advantage of relationship between two people that can be found in social media

**Distributing infected USB:**
- Distribute the usb in random places
- coffee shop, parking lots, or office
- or could be by mailing it to the office with the company logo

**Watering hole attack:**
- Compromising Website people usually visit
- Put little "harmless" emails pointing to the website
- After visiting the website, victims would unintentionally the malware or suspicious application

# Exploitation

- To gain access to the system
- This phase is exploiting vulnerabilities in the system of user itself
- Zero-day exploit: is often refer to an exploit that already caused problems before any signs arise

**This is how attacker carries out exploitation:**
- Victims clicks on email attachment or clicking on malicious link
- using zero day exploit
- exploit software, hardware or even human vulnerabilities
- attacker triggers exploit for server-based vulnerabilities

# Installation

- Installing an access points for an easier access if he loses connection 
- This is call **Persistent backdoor** which will let attacker access the system that has been compromised in the past

**This can be achieved through:**
- installing a web shell
	- written in web development programming language(PHP, ASP, JSP)
	- difficult to detect and might be classified as "harmless"
- Installing a backdoor on the victim's machine
- Creating or modifying window services
	- will use legitimate software operating systems
	- to alter the function of windows services
- Adding entry to the "run keys" for the payload at the registry or startup folder
	- will always run when computer starting
	- cant see shit

# Command & Control

- After getting persistence installed
- Attacker would start the C2(Command and Control)
- Infected host would consistently communicate with external server set up by attacker

**The most common C2 channels used by adversaries nowadays:**
- The HTTP protocol and HTTPS - blends in with legitimate traffic
- DNS - Make constants DNS requests with attacker DNS server, will make the infected host will always go to attacker

# Actions on Objective (Exfiltration)

- Will finally take the objectives

**The attacker would usually aims for the:**
- Collect credentials from the users
- perform privilege execution
- internal recon
- lateral movement through the company
- Collect and exfiltrate sensitive data
- Deleting backups and shadow copies
- Overwrite or corrupt data