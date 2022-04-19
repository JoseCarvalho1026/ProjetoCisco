## Switch14 Configuration  
### Port channel
```
interface Port-channel2
 switchport mode trunk
```
### Interfaces
```
interface FastEthernet0/4
 switchport access vlan 10
 switchport mode access

interface FastEthernet0/11
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active

interface FastEthernet0/12
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active

interface FastEthernet0/15
 switchport mode trunk
```
