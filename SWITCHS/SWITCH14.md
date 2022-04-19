## Switch14 Configuration 
### VTP
```
vtp domain enta.pt
```
### Port channel
```
interface Port-channel2
 no shutdown
 switchport mode trunk
```
### Interfaces
```
interface FastEthernet0/4
 no shutdown
 switchport access vlan 10
 switchport mode access

interface FastEthernet0/11
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active

interface FastEthernet0/12
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active

interface FastEthernet0/15
 no shutdown
 switchport mode trunk
```
