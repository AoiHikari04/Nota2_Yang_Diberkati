![[Pasted image 20241112090030.png]]
1. Peer ISP with eBGP
```
router bgp <AS-NUMBER>
neighbor <PEER IP> remote as <PEER-AS>
network <MY NETWORK>
```
1. Configure Local AAA , SSHv2
- ISP 
```
aaa new-model
username cisco password 0 cisco

ip domain-name cisco.com
crypto key generate rsa

```

```
ip ssh time-out 60
ip ssh authentication-retries 2
ip ssh version 2

```
- Only allow vlan 101 to access it
```

ip access-list standard SSH_ACCESS
permit 142.71.2.128 0.0.0.127
line vty 0 4
access-class SSH_ACCESS in
transport input ssh

```
- Verification
```
sh crypto key mypubkey rsa
show ip access-lists
show run | section line vty
show ssh
sh ip ssh

```
2. Configure DSW4
```

int range g0/0-2
no negotiation auto
duplex full
sw tru encapsulation dot1q
sw mode tru
sw trunk allowed vlan 1-1005

int range g0/3 , g1/0
sw mode acc

vtp mode client
vtp domain DSW
vtp password cisco

int g0/3
sw acc vlan 102
int g1/0
sw acc vlan 101

```

4. Enable port security
- DSW4
```
int range g0/3 , g1/0
sw port-security
sw port max 1
switchport port-security violation restrict
sw port mac sticky
```
5. Change native vlan to 99 to all L2 , L3

- DSW1
```
vlan database
vlan 99
apply 
abort

int range port 1 , f3/2 , f3/0
switchport trunk native vlan 99
```

- DSW2
```
int range port 1 , f3/1 - 2
switchport trunk native vlan 99
```

- DSW3 
```
int range f3/0  , f3/4
switchport trunk native vlan 99
```

- DSW4 
```
int range g0/0 - 1
switchport trunk native vlan 99
```

- Verification 
```
sh int tru
```

6. Spanning tree port -fast , BPDU guard on 

- DSW3
```
int range f3/2 - 3
sw mode acc
span portfast
spanning-tree portfast bpduguard
no shut
```

- Verification
```
sh span sum
```
7. DHCP server
- R1(R2)
```
ip dhcp excluded-address 142.71.2.1 142.71.2.10

ip dhcp pool DHCP_VLAN102
network 142.71.2.0 255.255.255.128
default-router 142.71.2.5
dns-server 142.71.2.6
domain-name lab5.com

```

- DSW1 
```
service dhcp

int vlan 102
ip helper-address 142.71.3.5
```
- DSW2
```
service dhcp
int vlan 102
ip helper-address 142.71.3.9
```
- Verification 
```
sh ip dhcp binding
sh ip dhcp pool
```

8. IP dhcp snooping and DAI on DSW4
- DSW4
```
ip dhcp snooping
ip dhcp snooping vlan 102
ip arp inspection vlan 102

int range g0/0 - 1
ip dhcp snooping trust
ip arp inspection trust
```

- Verification
```
show ip dhcp snooping
show ip arp inspection
```
## Reference 
- [Cisco](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/sec_usr_ssh/configuration/xe-16/sec-usr-ssh-xe-16-book/sec-secure-shell-v2.html)
- https://www.cisco.com/c/en/us/support/docs/security-vpn/secure-shell-ssh/4145-ssh.html

## Comment
- Check balik snooping boleh ke trust semua orang