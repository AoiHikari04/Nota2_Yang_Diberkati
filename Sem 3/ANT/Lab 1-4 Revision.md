

![[Lab1.jpg]]

First of all lets define IP address for each Vlan

**VLAN 101**
142.70.101.0
255.255.255.128
2001:142:70:101::1/64

**VLAN 102**
142.70.102.0
255.255.255.128
2001:142:70:102::1/64

**VLAN 103**
142.70.3.0
255.255.254.0
2001:142:70:103::1/64

1. Let start with enabling vtp for all switches
```
en


conf t


vtp dom vtpserver


vtp pass cisco 


vtp mode client
```

2. Before setting ip lets enable IPv6 first for all switches

```

conf t
ipv6 uni
ip routing

```


3. Set corresponding port into trunk mode


```

int ran f3/0 - 2 
switchport mode trunk
sw trunk allow vlan all

int f3/4
switchport mode acc

```


4. Now lets set ip address for each vlan on switch 1
```

conf t

vlan 103
name VLAN103

int vlan 103
ip add 142.70.0.1 255.255.254.0
ipv6 add 2001:142:70:103::1/64
ipv6 en
no shut

vlan 102
name VLAN102

int vlan 102
ip add 142.70.2.1 255.255.255.128
ipv6 add 2001:142:70:102::1/64
ipv6 en
no shut

vlan 101
name VLAN101

int vlan 101
ip add 142.70.3.1 255.255.255.128
ipv6 add 2001:142:70:101::1/64
ipv6 en
no shut




```

5. Now let set Spanning-tree Protocol

- switch 1

```

conf t

spanning-tree vlan 101 root prim
spanning-tree vlan 102 root secondary
spanning-tree vlan 103 root prim

```

- switch 2

```

conf t

spanning-tree vlan 101 root secondary
spanning-tree vlan 102 root prim
spanning-tree vlan 103 root secondary

```

- switch 3 & 4
```

conf t

spanning-tree vlan 101 root secondary
spanning-tree vlan 102 root secondary
spanning-tree vlan 103 root secondary

```

6.  PC IP add

- vlan 101

```

ip 142.70.3.5/25 142.70.3.1
ip 2001:142:70:101::5/64 2001:142:70:101::1

```

- vlan 102

```

ip 142.70.2.5/25 142.70.2.1
ip 2001:142:70:102::5/64 2001:142:70:102::1

```

- vlan 103

```

ip 142.70.0.5/25 142.70.0.1
ip 2001:142:70:103::5/64 2001:142:70:103::1

```



settle for lab 1

## LAB 2

![[Pasted image 20241203140928.png]]

OBJECTIVES
- configure HSRP with tracking
- configure Etherchannel
- assign loopback to router
- create static routes

0. dun forget to enable ip routing and ipv6 unicast
```
conf t
ip routing
ipv6 uni

```

1. first lets configure the Etherchannel between switch 1 and 2
```

conf t

int rang f3/0 , f3/3
sw mode trunk
channel-group 1 mode on

```
- to validate channel group
```
sh ip int bri

sh etherchannel summary

sh int port-channel 1

```

2. next configure HSRP (template) Switch 1
```
int vlan 101
ip add 142.70.3.2 255.255.255.128
ipv6 add 2001:142:70:101::2/64
standby version 2

** for ipv4 **

standby 101 ip 142.70.3.1
standby 101 preempt
standby 101 priority 115
standby 101 track f1/0 15
standby 101 track f2/0 15

** for ipv6 **

standby 1 ipv6 fe80::101
standby 1 preempt
standby 1 priority 115
standby 1 track f1/0 15
standby 1 track f2/0 15

```
- just repeat for each ip address
	- but remember to change priority for vlan 102
```
int vlan 102
ip add 142.70.2.2 255.255.255.128
ipv6 add 2001:142:70:102::2/64
standby version 2

** for ipv4 **

standby 102 ip 142.70.2.1
standby 102 preempt
standby 102 priority 90
standby 102 track f1/0 15
standby 102 track f2/0 15

** for ipv6 **

standby 2 ipv6 fe80::102
standby 2 preempt
standby 2 priority 90
standby 2 track f1/0 15
standby 2 track f2/0 15

---------------------------------------------------------

int vlan 103
ip add 142.70.0.2 255.255.254.0
ipv6 add 2001:142:70:103::2/64
standby version 2

** for ipv4 **

standby 103 ip 142.70.0.1
standby 103 preempt
standby 103 priority 115
standby 103 track f1/0 15
standby 103 track f2/0 15

** for ipv6 **

standby 3 ipv6 fe80::103
standby 3 preempt
standby 3 priority 115
standby 3 track f1/0 15
standby 3 track f2/0 15

```

- now to Switch 2
	- do the same thing but change the priority
```
int vlan 101
ip add 142.70.3.3 255.255.255.128
ipv6 add 2001:142:70:101::3/64
standby version 2

** for ipv4 **

standby 101 ip 142.70.3.1
standby 101 preempt
standby 101 priority 90
standby 101 track f1/0 15
standby 101 track f2/0 15

** for ipv6 **

standby 1 ipv6 fe80::101
standby 1 preempt
standby 1 priority 90
standby 1 track f1/0 15
standby 1 track f2/0 15

------------------------------------------------------------------------------

int vlan 102
ip add 142.70.2.3 255.255.255.128
ipv6 add 2001:142:70:102::3/64
standby version 2

** for ipv4 **

standby 102 ip 142.70.2.1
standby 102 preempt
standby 102 priority 115
standby 102 track f1/0 15
standby 102 track f2/0 15

** for ipv6 **

standby 2 ipv6 fe80::102
standby 2 preempt
standby 2 priority 115
standby 2 track f1/0 15
standby 2 track f2/0 15

-----------------------------------------------------------------------------

int vlan 103
ip add 142.70.0.3 255.255.254.0
ipv6 add 2001:142:70:103::3/64
standby version 2

** for ipv4 **

standby 103 ipv6 142.70.0.1
standby 103 preempt
standby 103 priority 90
standby 103 track f1/0 15
standby 103 track f2/0 15

** for ipv6 **

standby 3 ip fe80::101
standby 3 preempt
standby 3 priority 90
standby 3 track f1/0 15
standby 3 track f2/0 15

```

3. Now lets create Loopback and also ip add for each port for the router 1

- before that lets make a table for the ip add and the concurrent port for the ip

| **Device** | **Interface** | **IPv4 Address** | **IPv6 Address**       | **Connected To** | IPv4 address     |
| ---------- | ------------- | ---------------- | ---------------------- | ---------------- | ---------------- |
| R2         | g0/0          | 142.70.10.1 / 30 | 2001:142:70:1::1 / 64  | g0/0 (r2)        | 142.70.10.2 / 30 |
| R2         | g1/0          | 142.70.11.1 / 30 | 2001:142:70:11::1 / 64 | f1/0 (sw 2)      | 142.70.11.2 / 30 |
| R2         | g2/0          | 142.70.12.1 / 30 | 2001:142:70:12::1 / 64 | f2/0(r2)         | 142.70.12.2 / 30 |
| R2         | L0            | 142.70.20.1 / 32 | 2001:142:70:20::1 / 64 | -                |                  |
| R1         | g0/0          | 142.70.13.1 / 30 | 2001:142:70:13::1 / 64 | f1/0 (sw 2)      | 142.70.13.2 / 30 |
| R1         | g1/0          | 142.70.14.1 / 30 | 2001:142:70:14::1 / 64 | f2/0 (sw 1)      | 142.70.14.2 / 30 |
| R1         | L0            | 142.70.20.2 / 32 | 2001:142:70:20::2 / 64 | -                |                  |


- router 2

```
int lo0
ipv6 enable
ip add 142.70.20.1 255.255.255.255
ipv6 add 2001:142:70:20::1/128
no shut

int g0/0
ipv6 en
ip add 142.70.10.1 255.255.255.252
ipv6 add 2001:142:70:10::1/64
no shut

int g1/0
ipv6 en
ip add 142.70.11.1 255.255.255.252
ipv6 add 2001:142:70:11::1/64
no shut

int g2/0
ipv6 en
ip add 142.70.12.1 255.255.255.252
ipv6 add 2001:142:70:12::1/64
no shut

```

- do the same for router 1

```
int lo0
ipv6 enable
ip add 142.70.20.2 255.255.255.255
ipv6 add 2001:142:70:20::2/128
no shut

int g0/0
ipv6 en
ip add 142.70.10.2 255.255.255.252
ipv6 add 2001:142:70:10::2/64
no shut

int g1/0
ipv6 en
ip add 142.70.13.1 255.255.255.252
ipv6 add 2001:142:70:13::1/64
no shut

int g2/0
ipv6 en
ip add 142.70.14.1 255.255.255.252
ipv6 add 2001:142:70:14::1/64
no shut

```

- do the same for sw 1

```
int f1/0
ipv6 en
ip add 142.70.11.2 255.255.255.252
ipv6 add 2001:142:70:11::2/64
no shut

int f2/0
ipv6 en
ip add 142.70.14.2 255.255.255.252
ipv6 add 2001:142:70:14::2/64
no shut


```

- and also sw 2

```
int f1/0
ipv6 en
ip add 142.70.13.2 255.255.255.252
ipv6 add 2001:142:70:13::2/64
no shut

int f2/0
ipv6 en
ip add 142.70.12.2 255.255.255.252
ipv6 add 2001:142:70:12::2/64
no shut

```

4. lastly create the static route to Loopback for each router
- router 2
```
ip route 142.70.20.2 255.255.255.255 142.70.10.2
ipv6 route 2001:142:70:20::2/128 2001:142:70:10::2

ip route 0.0.0.0 0.0.0.0 142.70.11.2
ipv6 route ::0/0 2001:142:70:11::2

```
- router 1
```
ip route 142.70.20.1 255.255.255.255 142.70.10.1
ipv6 route 2001:142:70:20::1/128 2001:142:70:10::1

ip route 0.0.0.0 0.0.0.0 142.70.13.2
ipv6 route ::0/0 2001:142:70:13::2

```
- sw1
```

ip route 142.70.20.1 255.255.255.255 142.70.11.1 
ip route 142.70.20.2 255.255.255.255 142.70.14.1

ipv6 route 2001:142:70:20::1/64 2001:142:70:11::1
ipv6 route 2001:142:70:20::2/64 2001:142:70:14::1

```
- sw 2
```

ip route 142.70.20.1 255.255.255.255 142.70.12.1 
ip route 142.70.20.2 255.255.255.255 142.70.13.1

ipv6 route 2001:142:70:20::1/64 2001:142:70:12::1
ipv6 route 2001:142:70:20::2/64 2001:142:70:13::1

```

Done for lab 2

## LAB 3

![[Pasted image 20241203171002.png]]

Objectives
- configure Etherchannel between R3 and R2
- static route between ISP and R1 & static null to prevent looping
- remove all prev static conf
- conf ospf with md5 auth
- configure R1 to be default

0. IP ADDR and the corresponding port

| **Device** | **Interface** | **IPv4 Address**  | **IPv6 Address**         | **Connected To**  | IPv4 address      |
| ---------- | ------------- | ----------------- | ------------------------ | ----------------- | ----------------- |
| R2         | port-channel  | 142.70.15.1 / 30  | 2001:142:70:15::1 / 64   | port-channel (r3) | 142.70.15.2 / 30  |
| R3         | g0/0          | 142.70.16.1 / 30  | 2001:142:70:11::1 / 64   | f1/0 (sw 2)       | 142.70.11.2 / 30  |
| R3         | L0            | 142.70.20.3 / 32  | 2001:142:70:20:3 / 128   | -                 | -                 |
| R1         | g3/0          | 100.100.70.1 / 30 | 2001:100:100:70::1 / 127 | g3/0 (ISP)        | 100.100.70.2 / 30 |
| ISP        | Lo0           | 150.100.0.1 / 16  | 2001:150:100::1 /48      | -                 | -                 |
| Sw3        | vlan 104      | 142.70.4.1 / 26   | 2001:142:70:104::1 /64   |                   |                   |


0. Configure ISP

```
conf t

ip routing
ipv6 uni

int Lo0
ip add 150.100.0.1 255.255.0.0 
ipv6 add 2001:150:100::1/48
ipv6 en
no shut

int g3/0
ip add 100.100.70.2 255.255.255.252 
ipv6 add 2001:100:100:70::/127
ipv6 en
no shut

```
- Router 1
```

int g3/0
ip add 100.100.70.1 255.255.255.252
ipv6 add 2001:100:100:70::1/127
ipv6 en
no shut

```

1. Lets start with configuring EtherChannel for R3 and R2
```

int port-channel 1
ip add  142.70.15.2 255.255.255.252
ipv6 add 2001:142:70:15::2/64
ipv6 en
no shut

int ran g3/0 , g4/0
channel-group 1
no shut

```

2. Lets remove all the previous static route ( can skip )
- router 2
```

no ip route 142.70.20.2 255.255.255.255 142.70.10.2
no ipv6 route 2001:142:70:20::2/128 2001:142:70:10::2

no ip route 0.0.0.0 0.0.0.0 142.70.11.2
no ipv6 route ::0/0 2001:142:70:11::2

```
- router 1
```
no ip route 142.70.20.1 255.255.255.255 142.70.10.1
no ipv6 route 2001:142:70:20::1/128 2001:142:70:10::1

no ip route 0.0.0.0 0.0.0.0 142.70.13.2
no ipv6 route ::0/0 2001:142:70:13::2

```
- sw1
```

no ip route 142.70.20.1 255.255.255.255 142.70.11.1 
no ip route 142.70.20.2 255.255.255.255 142.70.14.1

no ipv6 route 2001:142:70:20::1/64 2001:142:70:11::1
no ipv6 route 2001:142:70:20::2/64 2001:142:70:14::1

```
- sw 2
```

no ip route 142.70.20.1 255.255.255.255 142.70.12.1 
no ip route 142.70.20.2 255.255.255.255 142.70.13.1

no ipv6 route 2001:142:70:20::1/64 2001:142:70:12::1
no ipv6 route 2001:142:70:20::2/64 2001:142:70:13::1

```

3. lets configure static route for ISP and R2
- router 1
```

ip route 150.100.0.0 255.255.0.0 100.100.70.2
ipv6 route 2001:150:100::/48 2001:100:100:70::2

ip route 142.70.0.0 255.255.0.0 null0
ipv6 route 2001:142:70::/48 null 0

```
- ISP
```

ip route 142.70.0.0 255.255.0.0 100.100.70.1
ipv6 route 2001:142:70::/48 2001:100:100:70::1

ip route 150.100.0.0 255.255.0.0 null0
ipv6 route 2001:150:100::/48 null0

```

4. Configure Router 3 and switch 3

- router 3
```

ip routing
ipv6 uni

int Lo0
ip add 142.70.20.3 255.255.255.255 
ipv6 add 2001:142:70:20::3/128
ipv6 en
no shut

int g0/0
ip add 142.70.16.1 255.255.255.252
ipv6 add 2001:142:70:16::1/64
ipv6 en 
no shut

```

- switch 3

```
conf t

ip routing
ipv6 uni

int f1/0
ip add 142.70.16.2 255.255.255.252
ipv6 add 2001:142:70:16::2/64
ipv6 en
no shut

int vlan 104
ip add 142.70.4.1 255.255.255.192
ipv6 add 2001:142:70:104::1/64
ipv6 en
no shut

ip route 0.0.0.0 0.0.0.0 142.70.16.1
ipv6 route ::0/0 2001:142:70:16::1

int f3/0
switchport mode acc
swi acc vlan 104
no shut

```

5. Configure OSPF
- Router 1
```

conf t
router ospf 10
router-id 1.1.1.1
network 142.70.10.0 0.0.0.3 area 0 
network 142.70.13.0 0.0.0.3 area 0 
network 142.70.14.0 0.0.0.3 area 0 
network 100.100.70.0 0.0.0.3 area 0
network 142.70.20.2 0.0.0.0 area 0 

default-info originate always

ipv6 router ospf 10
default-info originate always

passive g3/0

int ran g3/0 , g2/0 , g1/0 , g0/0 , lo0
ip ospf 10 area 0
ipv6 ospf 10 area 0
ip ospf message-digest-key 1 md5 cisco123


```

- router 2

```

router ospf 10
router-id 2.2.2.2
network 142.70.10.0 0.0.0.3 area 0 
network 142.70.11.0 0.0.0.3 area 0 
network 142.70.12.0 0.0.0.3 area 0 
network 142.70.20.1 0.0.0.0 area 0 
network 142.70.15.0 0.0.0.3 area 50

int ran g2/0 , g1/0 , g0/0, lo0
ip ospf 10 area 0
ipv6 ospf 10 area 0
ip ospf message-digest-key 1 md5 cisco123

int port-channel 1
ip ospf 10 area 50
ipv6 ospf 10 area 50
ip ospf message-digest-key 1 md5 cisco123


```

- Switch 1

```

router ospf 10
router-id 4.4.4.4
network 142.70.0.0 0.0.1.255 area 0
network 142.70.2.0 0.0.0.127 area 0
network 142.70.3.0 0.0.0.127 area 0

network 142.70.11.0 0.0.0.3 area 0
network 142.70.14.0 0.0.0.3 area 0

passive f3/0
passive f3/1
passive f3/2
passive f3/3

int ra f1/0 , f2/0
ip ospf 10 area 0
ipv6 ospf 10 area 0
ip ospf message-digest-key 1 md5 cisco123

int ran vlan 101 - 103
ip ospf 10 area 0
ipv6 ospf 10 area 0
ip ospf message-digest-key 1 md5 cisco123



```

- switch 2

```
router ospf 10
router-id 5.5.5.5
network 142.70.0.0 0.0.1.255 area 0
network 142.70.2.0 0.0.0.127 area 0
network 142.70.3.0 0.0.0.127 area 0

network 142.70.12.0 0.0.0.3 area 0
network 142.70.13.0 0.0.0.3 area 0

passive f3/0
passive f3/1
passive f3/2
passive f3/3

int ra f1/0 , f2/0
ip ospf 10 area 0
ipv6 ospf 10 area 0
ip ospf message-digest-key 1 md5 cisco123

int ran vlan 101 - 103
ip ospf 10 area 0
ipv6 ospf 10 area 0
ip ospf message-digest-key 1 md5 cisco123

```

- router 3

```
router ospf 10
router-id 3.3.3.3
network 142.70.16.0 0.0.0.3 area 50
network 142.70.15.0 0.0.0.3 area 50
network 142.70.20.3 0.0.0.0 area 50

network 142.70.4.0 0.0.0.63 area 50

int range port-channel 1 , g0/0 , lo0 
ip ospf 10 area 50
ipv6 ospf 10 area 50
ip ospf message-digest-key 1 md5 cisco123



```

- switch 3

```

router ospf 10
router-id 6.6.6.6
network 142.70.4.0 0.0.0.63 area 50

network 142.70.16.0 0.0.0.3 area 50

int f1/0
ip ospf 10 area 50
ipv6 ospf 10 area 50
ip ospf message-digest-key 1 md5 cisco123

int vlan 104
ip ospf 10 area 50
ipv6 ospf 10 area 50
ip ospf message-digest-key 1 md5 cisco123

```

6. configuration for MD5

- area 0
```
router ospf 10
area 0 authe message-digest
ipv6 router ospf 10
area 0 authe IPsec spi 256 md5 07982c55db2b9985d3391f02e639db9c

```

- area 50
```
router ospf 10
area 50 authe message-digest
ipv6 router ospf 10
area 50 authe IPsec spi 257 md5 07982c55db2b9985d3391f02e639db9c

```

### LAB 4
![[Pasted image 20241207135008.png]]

OBJECTIVE:
- Configure ipv4 PAT
- remove static route, configure BGP

| **Device** | **Interface**      | **IPv4 Address**   | **IPv6 Address**       | **Connected To** | IPv4 address  |
| ---------- | ------------------ | ------------------ | ---------------------- | ---------------- | ------------- |
| R3         | VLAN 105 (public)  | 142.70.5.1 / 30    | 2001:142:70:15::1 / 64 | -                | -             |
| R3         | VLAN 105 (private) | 192.168.0.0 / 25   | -                      | -                | -             |
| DSW6       | f0/0               | 192.168.100.2 / 30 | -                      | g1/0             | 192.168.100.1 |

1. configure PAT for R3

```
int g1/0
ip nat inside 

int port 1
ip nat outside

ip nat pool pool1 142.70.5.1 142.70.5.1 prefix 30
ip nat pool pool2 142.70.5.2 142.70.5.2 prefix 30

access-list 1 permit 192.168.0.0 0.0.0.63
access-list 2 permit 192.168.0.0 0.0.0.63

ip nat inside source list 1 pool pool1 overload
ip nat inside source list 2 pool pool2 overload

int lo1
ip add 142.71.5.1 255.255.255.252
```

2. remove static route
- R1
```
no ip route 150.100.0.0 255.255.0.0 100.100.70.2
no ipv6 route 2001:150:100::/48 2001:100:100:70::2

no ip route 142.70.0.0 255.255.0.0 null0
no ipv6 route 2001:142:70::/48 null 0

```
- ISP
```
no ip route 142.70.0.0 255.255.0.0 100.100.70.1
no ipv6 route 2001:142:70::/48 2001:100:100:70::1

no ip route 150.100.0.0 255.255.0.0 null0
no ipv6 route 2001:150:100::/48 null0
```

3. configure eBGP

- R1
```
-- IPV4 --

router bgp 20
bgp router-id 1.1.1.1
neighbor 100.100.70.2 remote-as 21
network 142.70.0.0 mask 255.255.0.0

-- IPV6 --

bgp log-neighbor-changes
neighbor 2001:100:100:70::0 remote-as 21
address-family ipv6
neighbot 2001:100:100:70::0 activate
network 2001:142:70::/48

```

- ISP
```

-- IPV4 --

router bgp 21
bgp router-id 2.2.2.2
neighbor 100.100.71.1 remote-as 20
network 150.100.0.0 mask 255.255.0.0

ip route 150.100.0.0 255.255.0.0 null0

-- IPV6 --

router bgp 21
neighbor 2001:100:70::1 remote-as 20
address-family ipv6
neigbor 2001:100:100:70::1 activate
network 2001:150:100::/48

ipv6 route 2001:150:100::/48 null0

```

>` note: buat je ip route tu, untuk bagi boleh gune, jgn byk tanye`


4. configure switch 6 for PAT inside
```

int f0/0
ip add 192.168.100.2 255.255.255.252
no shut

int range f3/0 - 1
no shut

int vlan 1
ip add 192.168.0.1 255.255.255.128

ip routing 
ip route 0.0.0.0 0.0.0.0 192.168.100.1

```

5. configure ospf R3 for additional ip
```

router ospf 10
network 142.70.5.0 255.255.255.252 area 50
pass g4/0

int g4/0
ip add 192.168.100.1 255.255.255.252
no shut

ip route 192.168.0.0 255.255.0.0 192.168.100.2

```

Done lab 4

## LAB 5

![[Pasted image 20241209214054.png]]

Objective
- peer ISP with other group members using eBGP
- configure local AAA for sshv2
- vIOSL2
- enable port security
- change native vlan to 99
- enable spanning-tree portfast and bpdu guard
- dhcp
- ip dhcp snooping and DAI






