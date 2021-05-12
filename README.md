# Networking
## Архитектура сети.
````
Сеть office1
192.168.2.0/26 - dev
192.168.2.64/26 - test servers
192.168.2.128/26 - managers
192.168.2.192/26 - office hardware

Сеть office2
192.168.1.0/25 - dev
192.168.1.128/26 - test servers
192.168.1.192/26 - office hardware

Сеть central
192.168.0.0/28 - directors
192.168.0.32/28 - office hardware
192.168.0.64/26 - wifi

Office1 ---\
-----> Central --IRouter --> internet
Office2----/

Итого должны получится следующие виртуалки
inetRouter
centralRouter
office1Router
office2Router
centralServer
office1Server
office2Server
````
## Диапозоны сетей лабораторной работы.

### Сеть office1:
````
Подразделение: dev
Диапозон IP: 192.168.2.0/26
Адресов: 62
Broadcast: 192.168.2.63

Подразделение: test servers
Диапозон IP: 192.168.2.64/26
Адресов: 62
Broadcast: 192.168.2.127

Подразделение: managers
Диапозон IP: 192.168.2.128/26
Адресов: 62
Broadcast: 192.168.2.191

Подразделение: office hardware
Диапозон IP: 192.168.192.0/26
Адресов: 62
Broadcast: 192.168.2.255
````

### Сеть office2:
````
Подразделение: dev
Диапозон IP: 192.168.1.0/25
Адресов: 126
Broadcast: 192.168.1.127

Подразделение: test servers
Диапозон IP: 192.168.1.128/26
Адресов: 62
Broadcast: 192.168.1.191

Подразделение: office hardware
Диапозон IP: 192.168.1.191/26
Адресов: 62
Broadcast: 192.168.1.255
````
### Сеть central:
````
Подразделение: directors
Диапозон IP: 192.168.0.0/28
Адресов: 14
Broadcast: 192.168.0.15

Подразделение: office hardware
Диапозон IP: 192.168.0.32/28
Адресов: 14
Broadcast: 192.168.0.47

Подразделение: wi-fi
Диапозон IP: 192.168.0.64/26
Адресов: 62
Broadcast: 192.168.0.127

Свободная подсеть в Central: 192.168.0.16/28
````
## Проверка выполнения:

````
vagrant up
````
````
[vagrant@office1Server ~]$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=32.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=31.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=35.6 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=57 time=31.5 ms
^C
--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3006ms
rtt min/avg/max/mdev = 31.380/32.774/35.603/1.690 ms
[vagrant@office1Server ~]$ tracepath -n 8.8.8.8
 1?: [LOCALHOST]                                         pmtu 1500
 1:  192.168.2.1                                           3.240ms
 1:  192.168.2.1                                           1.845ms
 2:  192.168.20.2                                          5.837ms
 3:  192.168.255.1                                         5.710ms
^C
[vagrant@office1Server ~]$ ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=61 time=7.65 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=61 time=6.49 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=61 time=6.96 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=61 time=6.44 ms
^C
--- 192.168.1.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 6.449/6.889/7.653/0.495 ms
[vagrant@office1Server ~]$ tracepath -n 192.168.1.2
 1?: [LOCALHOST]                                         pmtu 1500
 1:  192.168.2.1                                           1.890ms
 1:  192.168.2.1                                           1.480ms
 2:  192.168.20.2                                          3.749ms
 3:  192.168.10.1                                          6.884ms
 4:  192.168.1.2                                           9.605ms reached
     Resume: pmtu 1500 hops 4 back 4
````


