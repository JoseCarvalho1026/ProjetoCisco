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
 no shutdown
 switchport mode trunk
```
### Interfaces
```
interface FastEthernet0/4
 no shutdown
 switchport access vlan 30
 switchport mode access

interface FastEthernet0/5
 no shutdown
 switchport mode access
 switchport voice vlan 20
 mls qos trust cos
 spanning-tree portfast

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

interface FastEthernet0/13
 no shutdown
 switchport mode trunk
```
