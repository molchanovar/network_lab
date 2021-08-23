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
iptables --table nat --list   - просмотр таблицы nat

Chain POSTROUTING (policy ACCEPT)                                                                          target     prot opt source               destination                                                       MASQUERADE  all  --  anywhere            !192.168.0.0/16 
```
