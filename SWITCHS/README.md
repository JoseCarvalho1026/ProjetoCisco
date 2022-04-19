```
hostname Switch7
!
vtp domain enta.pt
!
vlan 10
 name v10
!
vlan 20
 name v20
!
vlan 30
 name v30
!
spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 10 priority 24576
spanning-tree vlan 20 priority 28672
!
interface Port-channel1
 no shutdown
 switchport mode trunk
!interface FastEthernet0/3
 no shutdown
 switchport mode trunk
!     
interface FastEthernet0/4
 no shutdown
 switchport mode trunk
!
interface FastEthernet0/11
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
!
interface FastEthernet0/12
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
!
interface FastEthernet0/15
 no shutdown
 switchport mode trunk
```
```
hostname Switch9
!
vtp domain enta.pt
!
spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 20 priority 28672
spanning-tree vlan 30 priority 24576
!
vlan internal allocation policy ascending
!
interface Port-channel1
 no shutdown
 switchport mode trunk
!
interface FastEthernet0/11
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
!
interface FastEthernet0/12
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
!  
interface FastEthernet0/13
 no shutdown
 switchport mode trunk
```
```
hostname Switch11
!
vtp domain enta.pt
!
spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 30 priority 28672
!
interface Port-channel2
 no shutdown
 switchport mode trunk
!
interface FastEthernet0/4
 no shutdown
 switchport access vlan 30
 switchport mode access
!
interface FastEthernet0/5
 no shutdown
 switchport mode access
 switchport voice vlan 20
 mls qos trust cos
 spanning-tree portfast
!
interface FastEthernet0/11
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
!       
interface FastEthernet0/12
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
!
interface FastEthernet0/13
 no shutdown
 switchport mode trunk
```
```
hostname Switch14
!
vtp domain enta.pt
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface Port-channel2
 no shutdown
 switchport mode trunk
!
interface FastEthernet0/4
 no shutdown
 switchport access vlan 10
 switchport mode access
!
interface FastEthernet0/11
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
!
interface FastEthernet0/12
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
!
interface FastEthernet0/15
 no shutdown
 switchport mode trunk
```
