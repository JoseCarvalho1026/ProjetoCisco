## BETA Router Configuration  
### Tunnel encryption  
```
crypto isakmp policy 10
 encr aes 256
 authentication pre-share
 group 5
 lifetime 3600
  
crypto isakmp key Passw0rd address 2.8.0.1

crypto ipsec transform-set TRANS2 ah-sha-hmac esp-aes 256 esp-sha-hmac

crypto map MAPA 10 ipsec-isakmp 
 set peer 2.8.0.1
 set transform-set TRANS2 
 match address 101
``` 
### Tunnel with ENTA router 
```
interface Tunnel200
 no shutdown
 ip address 192.168.8.6 255.255.255.252
 tunnel source Serial0/1/1
 tunnel destination 2.8.0.1
``` 
### Interfaces
```
interface FastEthernet0/0
 no shutdown
 ip address 172.16.8.3 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
 duplex auto
 speed auto
 
interface Serial0/1/1
 no shutdown
 ip address 2.8.0.2 255.255.255.252
 ip nat outside
 ip virtual-reassembly in
 crypto map MAPA
```
### Routing
```
router eigrp 200
 network 172.16.8.0 0.0.0.255
 network 192.168.8.4 0.0.0.3
 redistribute static
 passive-interface FastEthernet0/0
```
### NAT
```
ip nat inside source list 1 interface Serial0/1/1 overload
ip nat inside source static tcp 172.17.8.2 80 2.8.0.2 80 
ip nat inside source static tcp 172.17.8.2 443 2.8.0.2 443
```
### Access List
```
access-list 1 permit 10.0.0.0 0.255.255.255
access-list 1 permit 172.16.0.0 0.15.255.255
access-list 1 permit 192.168.0.0 0.0.255.255
access-list 101 permit gre host 2.8.0.2 host 2.8.0.1
access-list 100 permit tcp any any eq www
access-list 100 permit tcp any any eq 443
access-list 100 permit ip any 2.8.0.0 0.0.0.3
```
