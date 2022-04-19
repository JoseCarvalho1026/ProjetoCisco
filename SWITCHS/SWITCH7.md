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
 switchport mode trunk
```
### Interfaces
```
interface FastEthernet0/3
 switchport mode trunk
       
interface FastEthernet0/4
 switchport mode trunk

interface FastEthernet0/11
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active

interface FastEthernet0/12
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active

interface FastEthernet0/15
 switchport mode trunk
```
