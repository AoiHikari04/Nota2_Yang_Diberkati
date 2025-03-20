Threat Actors

- Attacks possible from either side, inside and also outside
- data can be easily stolen by stealing the hardware instead of breaking the software
- Weak security could also lead to potential data leak

terms in Campus Area Network
- VPN - protects data in motion from the Campus Area Networks (CAN) to the outside world, ensure data confidentiality
- ASA Firewall - adaptive security appliance, stateful packet filtering 
- IPS - intrusion prevention system, continuously monitor incoming and outgoing traffic for malicious activity, logs information and attempts to block and report it
- Layer 3 Switches - provide secure reduntdant trucnk connections to layer 2 switches, can configure ACLs, DHCP Snooping, Dynamic Arp Inspection and IP source guard
- Layer 2 Switches - port connecting to end user devices, can configure port security, DHCP snooping, and 802.1X user auth (password/key to access)
- ESA/WSA - email and web security appliance, detects and prevents suspicious emails and websites
- AAA server - authenticate, authorisation, accounting, only allow people to do things they are allowed to do
- Hosts - End points, can install antivirus software,


---
![[Pasted image 20250320083906.png]]
SOHO networks
- establish small networks
- setup port security to prevent outsiders
- for wireless can use WPA data encryption
- Hosts/end user, should download antivirus and antimalware software
- combining these security measures to ensure strong defense

---

![[Pasted image 20250320083854.png]]
WAN
- setup ASA which is a stateful firewall at main site
- Use setup and secured device at the edge of each network
- establishes VPN tunnel to various branches

--- 
Data center networks
- connected via VPN with ASA devices and integrated data center switches
- Physical security are as important, fire alarms, sprinklers, braced server racks

can be divided into two areas:
- Outside perimeter security : fences, gates, continuous surveillance, benda2 dkt luaq
- Inside perimeter security: security traps, biometric access, exit sensors, benda2 dlm bangunan

---
Cloud Networks and Virtualization
☁️ **Cloud Computing vs. Virtualization (ELI5)**
People often mix up cloud computing and virtualization, but they are different:

- **Virtualization** 🖥️ → Splits one physical computer into multiple virtual machines (VMs), each running its own operating system.
- **Cloud Computing** ☁️ → Lets you access applications and services over the internet without worrying about the underlying hardware.

**🏢 Example:**
Imagine a big office building (a physical server).

- **Virtualization** = Divides the building into separate office spaces (VMs) so different companies can work in the same building.
- **Cloud Computing** = Instead of owning an office, you rent a workspace when needed (Google Drive, Dropbox, AWS).

📌 **Why Does This Matter?**
Cloud computing relies on virtualization to create flexible, scalable services.
Virtual Machines (VMs) can be attacked, just like physical computers, making security important.

Example attacks :
- Hyperjacking - hijack one VM and then use it as launch point to attack other devices
- Instant on activation - old devices that might have vulnerabilities
- Antivirus storms - attempt to download antivirus data files at the same times ???

--- 
evolving network border

- happens because a lot people BYOD to work
- Cisco device support Mobile Device Management features such:
	- Data encryption : only allows device that support data encryption can access network
	- PIN enforcement : force PIN authorisation on the devices
	- Data wipe : lost items can be remotely wipe 
	- Data Loss Prevention : prevents authorised device do stupid stuff with their devices
	- Jailbreak/Root detection : detect and restrict device that are rooted or jailbreak


