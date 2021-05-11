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

