## Switch7 Configuration  
### Spanning Tree 
```
spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 10 priority 24576
spanning-tree vlan 20 priority 28672
```
### Port channel 
```
interface Port-channel1
 no shutdown
 switchport mode trunk
```
### Interfaces
```
interface FastEthernet0/3
 no shutdown
 switchport mode trunk
       
interface FastEthernet0/4
 no shutdown
 switchport mode trunk

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

interface FastEthernet0/15
 no shutdown
 switchport mode trunk
```
