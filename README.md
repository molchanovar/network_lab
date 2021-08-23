# network_lab
test_office_net

## Sheme: 
```
Office1 ---\
                   -----> Central --IRouter --> internet
Office2----/
```

#### iptables cheat sheet
```
/sbin/service iptables save   - save config (Centos)
/etc/sysconfig/iptables       - config file
iptables --table nat --list   - просмотр таблицы nat
iptables -t nat -A POSTROUTING ! -d 192.168.0.0/16 -o eth0 -j MASQUERADE   - пропуск трафика через сервер (+ net.ipv4.conf.all.forwarding=1)

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  anywhere            !192.168.0.0/16
```

#### network
```
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.0.2.2        0.0.0.0         UG        0 0          0 eth0
10.0.2.0        0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0     192.168.255.2   255.255.0.0     UG        0 0          0 eth1
192.168.255.0   0.0.0.0         255.255.255.252 U         0 0          0 eth1
```
