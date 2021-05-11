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
