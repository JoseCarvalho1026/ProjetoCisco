## ASA Configuration  
### Interfaces 
```
interface GigabitEthernet1/1
 no shutdown
 bridge-group 1
 nameif outside1
 security-level 0

interface GigabitEthernet1/2
 no shutdown
 bridge-group 2
 nameif inside1
 security-level 100

interface GigabitEthernet1/3
 no shutdown
 bridge-group 2
 nameif inside2
 security-level 100

interface GigabitEthernet1/4
 no shutdown
 nameif dmz
 security-level 50
 ip address 172.17.8.1 255.255.255.0 
 
interface GigabitEthernet1/5
 no shutdown
 bridge-group 1
 nameif outside2
 security-level 0

interface BVI1
 no shutdown
 nameif inside
 security-level 100
 ip address 172.18.8.1 255.255.255.0 

interface BVI2
 no shutdown
 nameif outside
 security-level 0
 ip address 172.16.8.1 255.255.255.0 
```
### Access List
```
access-list INTERNET extended permit icmp any any echo-reply 
access-list INTERNET extended permit udp any eq domain any 
access-list INTERNET extended permit tcp any eq www any 
access-list INTERNET extended permit tcp any eq https any 
access-list INTERNET extended permit tcp any any eq www 
access-list INTERNET extended permit tcp any any eq https 
access-list INTERNET extended permit icmp any any 
access-list DMZ extended permit ip any 172.17.8.0 255.255.255.0 
access-list DMZ extended permit tcp any eq www any 
access-list DMZ extended permit tcp any any eq www 
access-list DMZ extended permit udp any any eq domain 
access-list DMZ extended permit icmp any any 
access-list DMZ extended permit tcp any any eq https 
access-list DMZ extended permit tcp any eq https any 
access-list OUTSIDE extended permit icmp any any 
access-list OUTSIDE extended permit ip any any 
```
### Access Group
```
access-group DMZ in interface dmz
access-group OUTSIDE out interface inside
access-group INTERNET in interface outside
```
### NAT
```
object network HTTP
 nat (dmz,outside1) static 1.8.0.2
object network dmz
 nat (dmz,outside1) dynamic interface
object network HTTPS
 nat (dmz,outside2) static 1.8.0.2
object network dmz1
 nat (dmz,outside2) dynamic interface
object network inside
 nat (inside1,outside1) dynamic interface
object network inside1
 nat (inside2,outside1) dynamic interface
```
### DHCP
```
dhcpd dns 8.8.8.8
dhcpd address 172.18.8.2-172.18.8.10 inside
dhcpd option 150 ip 172.18.8.1 interface inside
dhcpd enable inside

ftp mode passive
object network HTTP
 host 172.17.8.254
object network dmz
 subnet 172.17.8.0 255.255.255.0
object network HTTPS
 host 172.17.8.254
object network dmz1
 subnet 172.17.8.0 255.255.255.0
object network inside
 subnet 172.16.0.0 255.240.0.0
object network inside1
 subnet 172.16.0.0 255.240.0.0
```
