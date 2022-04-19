## Switch9 Configuration
### VTP
```
vtp domain enta.pt
```
### Spanning Tree
```
spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 20 priority 28672
spanning-tree vlan 30 priority 24576
```
### Port channel
```
interface Port-channel1
 no shutdown
 switchport mode trunk
```
### Interfaces
```
interface FastEthernet0/11
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active

interface FastEthernet0/12
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
     
interface FastEthernet0/13
 no shutdown
 switchport mode trunk
```
