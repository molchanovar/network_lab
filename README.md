# Network_lab
## Architecture 

#### Сеть office1

- 192.168.2.0/26 - dev
- 192.168.2.64/26 - test servers
- 192.168.2.128/26 - managers
- 192.168.2.192/26 - office hardware

#### Сеть office2

- 192.168.1.0/25 - dev
- 192.168.1.128/26 - test servers
- 192.168.1.192/26 - office hardware

#### Сеть central

- 192.168.0.0/28 - directors
- 192.168.0.32/28 - office hardware
- 192.168.0.64/26 - wifi

### Nodes: 
- inetRouter
- centralRouter
- office1Router
- office2Router
- centralServer
- office1Server
- office2Server

## Sheme: 
```
Office1 ---\
                   -----> Central --IRouter --> internet
Office2----/
```

#### iptables cheats
```
/sbin/service iptables save   - save config (Centos)
/etc/sysconfig/iptables       - config file
iptables --table nat --list   - просмотр таблицы nat
iptables -t nat -A POSTROUTING ! -d 192.168.0.0/16 -o eth0 -j MASQUERADE   - пропуск трафика через сервер (+ net.ipv4.conf.all.forwarding=1)

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  anywhere            !192.168.0.0/16
```
#### Network
```
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.0.2.2        0.0.0.0         UG        0 0          0 eth0
10.0.2.0        0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0     192.168.255.2   255.255.0.0     UG        0 0          0 eth1
192.168.255.0   0.0.0.0         255.255.255.252 U         0 0          0 eth1
```
