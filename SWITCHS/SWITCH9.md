## Switch9 Configuration  
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
 switchport mode trunk
```
### Interfaces
```
interface FastEthernet0/11
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active

interface FastEthernet0/12
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
     
interface FastEthernet0/13
 switchport mode trunk
```
