#### 2 Лабораторная работа №2. Базовая настройка IP-телефонов в среде Cisco Packet Tracer
Цель работы: изучить построение сети IP-телефонии с помощью маршрутизатора, коммутатора и IP телефонов Cisco 7960 в среде Packet tracer.

Создаём схему соединения:

<img width="688" height="446" alt="image" src="https://github.com/user-attachments/assets/ac2fe0fc-d643-46ec-aa29-016ff83c7f29" />

*Схема соединения IP – телефонов с маршрутизатором через коммутатор*

1) Изменяем имя маршрутизатора на CMERouter.

<img width="316" height="35" alt="image" src="https://github.com/user-attachments/assets/485ce061-0cb6-4203-9620-4b4ec9928b0d" />

Отключаем синтаксис ввода слов от DNS серверов:

<img width="342" height="39" alt="image" src="https://github.com/user-attachments/assets/ad1ce8d6-e655-436d-b4bf-aea5b75404d3" />

2) Настраиваем интерфейс	fa0/0	на	CMERouter.

<img width="598" height="187" alt="image" src="https://github.com/user-attachments/assets/a9794b5d-4cb4-43a5-b6dc-d5d333f9837b" />

3) Настраиваем DHCP	сервера

<img width="474" height="74" alt="image" src="https://github.com/user-attachments/assets/6b941527-b967-4ac7-b703-527fd95e9be9" />

4) Настраиваем	услуги	телефонии	Cisco	CallManager	Express	на CMERouter.

<img width="582" height="140" alt="image" src="https://github.com/user-attachments/assets/f9f6aa2e-03cc-4ff5-a67e-1d4b7b62c92f" />

5) Настраиваем VLAN на интерефейсах SwitchA

<img width="403" height="107" alt="image" src="https://github.com/user-attachments/assets/61ce9f81-1c83-4321-b8ae-f5b975489d6b" />

6) Создаем логическую линию, а так же выполняем настройку номеров телефонов

<img width="613" height="194" alt="image" src="https://github.com/user-attachments/assets/80be96ad-6aed-488c-8d8e-70edb4f2415b" />


Конфигурация устройств:

#### CMERouter

Current configuration : 949 bytes

!

version 15.1

no service timestamps log datetime msec

no service timestamps debug datetime msec

no service password-encryption

!

hostname CMERouter

!

!

!

!

!

ip dhcp pool VOICE

 network 192.168.10.0 255.255.255.0

 default-router 192.168.10.1

 option 150 ip 192.168.10.1

!

!

!

ip cef

no ipv6 cef

!

!

!

!

license udi pid CISCO2811/K9 sn FTX1017CSJ1-

!

!

!

!

!

!

!

!

!

no ip domain-lookup

!

!

spanning-tree mode pvst

!

!

!

!

!

!

interface FastEthernet0/0

 ip address 192.168.10.1 255.255.255.0

 duplex auto
 
 speed auto

!

interface FastEthernet0/1

 no ip address

 duplex auto

 speed auto

 shutdown

!

interface Vlan1
 
 no ip address

 shutdown

!

ip classless

!

ip flow-export version 9

!

!

!

no cdp run

!

!

!

!

!

!

telephony-service

 max-ephones 5

 max-dn 5

 ip source-address 192.168.10.1 port 2000

 auto assign 4 to 6

 auto assign 1 to 5

!

ephone-dn 1

 number 54001

!

ephone-dn 2

 number 54001

!

line con 0

!

line aux 0

!

line vty 0 4

 login

!

!

!

end


#### SwitchA
``
Building configuration...
Current configuration : 1325 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
 switchport mode access
 switchport voice vlan 1
!
interface FastEthernet0/2
 switchport mode access
 switchport voice vlan 1
!
interface FastEthernet0/3
 switchport mode access
 switchport voice vlan 1
!
interface FastEthernet0/4
 switchport mode access
 switchport voice vlan 1
!
interface FastEthernet0/5
 switchport mode access
 switchport voice vlan 1
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 no ip address
 shutdown
!
!
!
!
line con 0
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end
``


#### Контрольные вопросы

1. Принцип работы протокола SIP?
SIP (Session Initiation Protocol)-протокол установления сеанса связи. Он работает по принципу клиент-сервер и использует текстовые запросы. SIP отвечает за обнаружение абонента, установление соединения, подтверждение, изменение параметров сеанса и завершение звонка. Голосовой трафик передается отдельно по протоколу RTP.

2. Как создается VLAN для голосового трафика?
На коммутаторе создается отдельный VLAN, после чего на порту, к которому подключен IP-телефон, задаются две команды:
- switchport mode access — порт работает в режиме доступа.
- switchport voice vlan <номер> — указывается VLAN для голосового трафика.
При этом телефон получает данные в access VLAN, а голос — в voice VLAN.

3. Система Cisco Call Manager?
Cisco Unified Call Manager-это программная платформа для IP-телефонии корпоративного уровня, работающая на выделенных серверах. Поддерживает тысячи абонентов, резервирование, расширенные функции (очереди, голосовая почта). Требует лицензирования и отдельной инфраструктуры.

4. Система Cisco Call Manager Express?
CME-это встроенная в маршрутизаторы Cisco (например, 2811) упрощенная система IP-телефонии. Поддерживает до небольших сотен абонентов (для 2811 — до 96 телефонов). Настраивается через CLI, не требует отдельного сервера, идеальна для малых и средних офисов.

5. Чем отличается Cisco Call Manager от Cisco Call Manager Express?
CUCM: серверная платформа, тысячи абонентов, высокая отказоустойчивость, централизованное управление через веб-интерфейс.
CME: встроена в маршрутизатор, до ~240 абонентов, настройка через CLI, ограниченный функционал, TFTP-сервер на самом маршрутизаторе.

6. Что дает команда spanning-tree portfast?
Команда переводит порт коммутатора в режим быстрого перехода в состояние forwarding, пропуская стадии listening и learning.
Используется на портах, подключенных к конечным устройствам, чтобы они получали связь сразу после включения, а не через 30–50 секунд.

8. Требования к сети при передаче голосового трафика?
1 Низкая задержка.
2 Низкие джиттер.
3 Минимальные потери пакетов.
4 Приоритезация голоса-например, через CoS или DSCP.
5 Достаточная пропускная способность.
6 Отсутствие коллизий в сегменте Ethernet.

9. Основные команды конфигурирования DHCP сервера на маршрутизаторе?
1 ip dhcp excluded-address <начало> <конец> — исключение адресов (например, шлюза).
2 ip dhcp pool <имя> — создание пула.
3 network <сеть> <маска> — задание сети.
4 default-router <адрес> — указание шлюза по умолчанию.
5 option 150 ip <адрес> — указание TFTP-сервера (нужно для IP-телефонов с CME).
6 dns-server <адрес> — DNS-сервер (опционально).
7 lease <дни часы минуты> — время аренды.

#### 3	Лабораторная	работа	№3.	Настройка	конфигурации	Cisco CallManager Express на маршрутизаторе Cisco 2811
Цель работы: изучить построение сети IP-телефонии с помощью маршрутизатора Cisco 2811, коммутатора Cisco catalyst 3560 и IP телефонов Cisco 7960.
