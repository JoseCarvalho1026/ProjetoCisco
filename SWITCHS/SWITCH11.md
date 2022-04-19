## Switch11 Configuration  
### Spanning Tree 
```
spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 30 priority 28672
```
### Port channel
```
interface Port-channel2
 switchport mode trunk
```
### Interfaces
```
interface FastEthernet0/4
 switchport access vlan 30
 switchport mode access

interface FastEthernet0/5
 switchport mode access
 switchport voice vlan 20
 mls qos trust cos
 spanning-tree portfast

interface FastEthernet0/11
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
        
interface FastEthernet0/12
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active

interface FastEthernet0/13
 switchport mode trunk
```
