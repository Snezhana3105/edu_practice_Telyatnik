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
```
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

```
#### SwitchA
```

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
```


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

## 3	Лабораторная	работа	№3.	Настройка	конфигурации	Cisco CallManager Express на маршрутизаторе Cisco 2811
Цель работы: изучить построение сети IP-телефонии с помощью маршрутизатора Cisco 2811, коммутатора Cisco catalyst 3560 и IP телефонов Cisco 7960.
1) Строим топологию сети

<img width="556" height="408" alt="image" src="https://github.com/user-attachments/assets/62820e80-11c3-419a-8732-6cdcb8dc724a" />

2) Меняем название	маршрутизатора на CMERouter.

<img width="307" height="42" alt="image" src="https://github.com/user-attachments/assets/ce7ba5d2-34e2-4367-9dc3-939d16cef345" />

Отключаем синтаксис ввода слов от DNS серверов:

<img width="358" height="43" alt="image" src="https://github.com/user-attachments/assets/29fcd2c6-9ddc-4080-ba98-41897b21c0a9" />

3) Задаём	пароли	для	защиты	маршрутизатора как в удаленном режиме, так и в режиме консоли:

<img width="398" height="151" alt="image" src="https://github.com/user-attachments/assets/5727c771-381a-4545-980b-8847202e54c3" />

4)	Настроим	интерфейс	fa0/0	на	CMERouter.

<img width="614" height="183" alt="image" src="https://github.com/user-attachments/assets/5860dfba-5c1f-4b5b-89e0-9bae8a896904" />

5) Настраиваем DHCP	сервера

<img width="484" height="141" alt="image" src="https://github.com/user-attachments/assets/c0987417-2d68-42d1-bb1f-64bb0847941e" />

6) Настраиваем	услуги	телефонии	Cisco	CallManager	Express	на CMERouter.

<img width="580" height="168" alt="image" src="https://github.com/user-attachments/assets/3bf5385b-9194-4fcb-8699-8f9294452ee1" />

7) Настраиваем порты SwitchA

<img width="427" height="118" alt="image" src="https://github.com/user-attachments/assets/d316100e-a545-4658-b7e2-ddd888f585fc" />

8) Создаем логическую линию, а так же выполняем настройку номеров телефонов

<img width="786" height="303" alt="image" src="https://github.com/user-attachments/assets/2d98908d-b69f-4725-8993-c1d670230a72" />

9) Подключаем телефоны к питанию:

<img width="682" height="441" alt="image" src="https://github.com/user-attachments/assets/948ae96c-02ee-4f1b-890f-3a7ece833cf6" />

10) Выполняем звонок на внутренние номера

<img width="1383" height="658" alt="image" src="https://github.com/user-attachments/assets/858c3621-2f25-4700-862a-15fb96c23ebc" />

11) Выполняем ping на телефоны c CMERouter.

<img width="628" height="358" alt="image" src="https://github.com/user-attachments/assets/d700eb02-e632-492d-9516-b0acab1e7f48" />

Конфигурация устройств:

#### CMERouter
```

Building configuration...



Current configuration : 1312 bytes

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

license udi pid CISCO2811/K9 sn FTX1017C63W-

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

 number 54002

!

ephone-dn 3

 number 54003

!

ephone 1

 device-security-mode none

 mac-address 0006.2AB4.0B6B

 type 7960

 button 1:1

!

ephone 2

 device-security-mode none

 mac-address 00E0.B016.1872

 type 7960

 button 1:2

!

ephone 3

 device-security-mode none

 mac-address 0090.2123.1084

 type 7960

 button 1:3

!

line con 0

 password cisco

 logging synchronous

 login

!

line aux 0

!

line vty 0 4

 password cisco

 logging synchronous

 login

!

!

!

end
```

#### SwitchA
```
Building configuration...

Current configuration : 1501 bytes

!

version 12.2(37)SE1

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

!

!

!

!

!

!

!

!

!

!

!

!

!

!

spanning-tree mode pvst

!

!

!

!

!

!

interface FastEthernet0/1

 switchport mode access

 switchport nonegotiate

 switchport voice vlan 1

!

interface FastEthernet0/2

 switchport mode access

 switchport nonegotiate

 switchport voice vlan 1

!

interface FastEthernet0/3

 switchport mode access

 switchport nonegotiate

 switchport voice vlan 1

!

interface FastEthernet0/4

 switchport mode access

 switchport nonegotiate

 switchport voice vlan 1

!

interface FastEthernet0/5

 switchport mode access

 switchport nonegotiate

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

ip classless

!

ip flow-export version 9

!

!

!

!

!

!

!

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

!

end
```

#### Контрольные вопросы
1. Принцип работы протокола SIP?
SIP (Session Initiation Protocol)-протокол сигнализации прикладного уровня для установления, изменения и завершения сеансов связи. Он передаёт текстовые запросы (INVITE, ACK, BYE, REGISTER) по модели «клиент-сервер». Голосовой трафик передаётся отдельно по протоколу RTP.

2. Как создается VLAN для голосового трафика?
На коммутаторе в конфигурационном режиме для диапазона портов задаются команды switchport mode access и switchport voice vlan 1.

3. Система Cisco Call Manager?
Cisco Unified Call Manager-корпоративная платформа IP-телефонии, работающая на выделенных серверах. Поддерживает тысячи абонентов, кластеризацию, резервирование и расширенные функции.

4. Система Cisco Call Manager Express?
CME-телефонный сервис, встроенный в маршрутизатор, работающий в автоматическом диалоговом режиме. На маршрутизаторе Cisco 2811 максимальное количество телефонов-96, номеров-5. Включается командой telephony-service.

5. Чем отличается система Cisco Call Manager от системы Cisco Call Manager Express?
CUCM работает на отдельном сервере, поддерживает тысячи абонентов, управляется через веб-интерфейс. CME встроен в маршрутизатор, поддерживает до 240 абонентов, настраивается через CLI.

6. Что дает команда spanning-tree portfast?
Команда переводит порт коммутатора сразу в режим forwarding, пропуская стадии listening и learning, что ускоряет подключение конечных устройств.

7. Требования к сети при передаче голосового трафика?
Задержка не более 150 мс, джиттер не более 30 мс, потери пакетов не более 1%, приоритезация голоса через QoS, достаточная пропускная способность.

8. Основные команды конфигурирования DHCP сервера на маршрутизаторе?
ip dhcp pool VOICE-создание пула,
network 192.168.10.0 255.255.255.0-задание сети,
default-router 192.168.10.1-указание шлюза,
option 150 ip 192.168.10.1-опция для TFTP-сервера CME.

#### Лабораторная работа №4. Конфигурация VOIP в среде Cisco Packet Tracer
Цель	работы:	изучить	построение	сети	IP-телефонии,	научиться стандартной настройке технологии VOIP.

Создаём схему соединения:

<img width="708" height="521" alt="image" src="https://github.com/user-attachments/assets/0c898e40-a543-4c24-9240-3c845037834e" />

1) Создание vlan и присвоение им наименований. 

<img width="616" height="252" alt="image" src="https://github.com/user-attachments/assets/0d35cab2-cc5e-4e7a-8a63-7b7a931e1c8a" />

2) Настройка vlan 99:

<img width="520" height="180" alt="image" src="https://github.com/user-attachments/assets/27148c4f-f44a-4f19-8de5-8c5366fb760f" />

3) Задаём маршрут по умолчанию

<img width="468" height="121" alt="image" src="https://github.com/user-attachments/assets/1fc3dd68-7129-4a61-bcdd-6ac746299b20" />

4) Настройка интерфейса управления коммутатором в сети VLAN через назначение диапазона портов:

<img width="502" height="134" alt="image" src="https://github.com/user-attachments/assets/ab8e7f76-c593-47f1-ab5b-bfd664744fcc" />

5) Включаем интерфейс F0/0:

<img width="626" height="247" alt="image" src="https://github.com/user-attachments/assets/e19f7075-3cb4-4370-8eda-9fdc56f37f3d" />

6) Создаем логический подинтерфейсы для VLAN 10, VLAN 20, VLAN 99: 

<img width="620" height="180" alt="image" src="https://github.com/user-attachments/assets/1264eb8c-6426-4339-a8f3-6117bff04f5d" />

*Создание подинтерфейсов для VLAN 10*

<img width="617" height="176" alt="image" src="https://github.com/user-attachments/assets/914fe1b0-9594-4a5a-9359-5b6c90e72d97" />

*Создание подинтерфейсов для VLAN 20*

<img width="642" height="207" alt="image" src="https://github.com/user-attachments/assets/1c8f3088-6171-460a-9e2f-e742e9ef7e28" />

*Создание подинтерфейсов для VLAN 99*

7) Исключаем из пула адрес интерфейса маршрутизатора и DNS-сервера: 

<img width="560" height="47" alt="image" src="https://github.com/user-attachments/assets/f42dafac-102a-4a92-b7c3-d5ba49fc511f" />

8) Настраиваем	DHCP	сервера	для	передачи	голоса	и	данных	на маршрутизаторе Cisco 2811:

<img width="488" height="190" alt="image" src="https://github.com/user-attachments/assets/011106b2-4c6b-4ef8-a84e-613ff56aac22" />

9) Настройка телефонного сервиса в автоматическом режиме: 

<img width="564" height="97" alt="image" src="https://github.com/user-attachments/assets/33e98a84-b5ee-4ee4-b447-0d89f67353b2" />

10) Присваиваем номера для всех IP-телефонов в сети: 

<img width="649" height="244" alt="image" src="https://github.com/user-attachments/assets/b8b81acb-3e6a-4d13-aae0-6aeca4b29135" />

*Настройка данных телефонов*

<img width="581" height="237" alt="image" src="https://github.com/user-attachments/assets/ace12fa5-3c9c-4c43-b701-f02abf5f8c76" />

*Настройка данных телефонов*

Конфигурация устройств:
### Router0
```

Building configuration...

Current configuration : 1612 bytes

!

version 15.1

no service timestamps log datetime msec

no service timestamps debug datetime msec

no service password-encryption

!

hostname Router

!

!

!

!

ip dhcp excluded-address 192.168.10.1 192.168.10.9

ip dhcp excluded-address 192.168.20.1 192.168.20.9

!

ip dhcp pool Data

 network 192.168.10.0 255.255.255.0

 default-router 192.168.10.1

ip dhcp pool Voice

 network 192.168.20.0 255.255.255.0

default-router 192.168.20.1

 option 150 ip 192.168.20.1

!

!

!

ip cef

no ipv6 cef

!

!

!

!

license udi pid CISCO2811/K9 sn FTX1017XX2R-

!

!

!

!

!

!

!

!

!

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

 no ip address

 duplex auto

 speed auto

!

interface FastEthernet0/0.10

 encapsulation dot1Q 10

 ip address 192.168.10.1 255.255.255.0

!

interface FastEthernet0/0.20

 encapsulation dot1Q 20

 ip address 192.168.20.1 255.255.255.0

!

interface FastEthernet0/0.99

 encapsulation dot1Q 99 native

 ip address 192.168.99.1 255.255.255.0

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

!

!

!

!

!

telephony-service

 max-ephones 3

 max-dn 3

 ip source-address 192.168.20.1 port 2000

!

ephone-dn 1

 number 101

!

ephone-dn 2

 number 102

!

ephone-dn 3

 number 103

!

ephone 1

 device-security-mode none

 mac-address 00D0.D389.A321

 type 7960

 button 1:1

!

ephone 2

 device-security-mode none

 mac-address 00E0.F737.1C36

 type 7960

 button 1:2

!

ephone 3

 device-security-mode none

 mac-address 0005.5E34.7BE9

 type 7960

 button 1:3

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
```
### Switch0
```
Building configuration...

Current configuration : 1382 bytes

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

 switchport trunk native vlan 99

 switchport mode trunk

!

interface FastEthernet0/2

 switchport access vlan 20

 switchport mode access

!

interface FastEthernet0/3

 switchport access vlan 20

 switchport mode access

!

interface FastEthernet0/4

 switchport access vlan 20

 switchport mode access

!

interface FastEthernet0/5

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

interface Vlan99

 ip address 192.168.99.10 255.255.255.0

!

ip default-gateway 192.168.99.1

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
```
#### Контрольные вопросы
1. Что такое SIP-телефоны?
SIP-телефоны-это телефоны, работающие по протоколу SIP, которые позволяют совершать звонки через IP-сеть.

2. Что такое Voice over IP?
Это технология передачи голоса по IP-сетям.

3. VOIP – определение.
VoIP-это технология, которая обеспечивает передачу голоса в сетях с пакетной коммутацией по протоколу IP, частным случаем которых являются сети Интернет, а также другие IP-сети.

4. Где можно найти хороший источник информации о VOIP?
- Официальная документация Cisco (cisco.com)
- Книги: «IP телефония» Д. Коллинза, «Компьютерные сети» Э. Таненбаума
- Сайты: Habr, Cisco Networking Academy, IT-блоги на Medium
- RFC-документы


5. Что такое IP-телефон / IP телефоны?
IP-телефон-это устройство или программа, дающее возможность пользователю звонить на любой другой софтфон, мобильный или обычный телефон, используя передачу голоса по IP. VoIP-телефон может представлять собой простой программный софтфон или устройство, очень похожее на обычный телефон.

6. Что такое IP-телефония?
IP-телефония-это технология передачи голоса по IP-сетям.

7. Что такое VoIP-телефон?
VoIP-телефон-это то же, что IP-телефон-устройство или программа для звонков через Интернет.

8. Каким образом создается маршрут по умолчанию?
Маршрут по умолчанию задается командой ip default-gateway <адрес> в конфигурационном режиме коммутатора.
Например: Switch(config)# ip default-gateway 192.168.99.1.

#### Лабораторная работа №7. Построение сети IP-телефонии между удаленными маршрутизаторами в среде Cisco Packet Tracer
Цель работы: изучить построение сети IP-телефонии между удаленными филиалами с помощью маршрутизаторов Cisco 2811 и коммутаторов Cisco 2950Т.

Создаём схему соединения:

<img width="829" height="571" alt="image" src="https://github.com/user-attachments/assets/426b4f6c-e30f-487d-b1bb-23ac7b3767d8" />

1) Меняем	название	маршрутизаторов на RouterA и RouterB:

<img width="641" height="48" alt="image" src="https://github.com/user-attachments/assets/ec1731c1-3b96-4a11-8878-9f22cc8c6d78" />

2) Конфигурация интерфейса fa0/0 на RouterA и RouterB: 

<img width="1177" height="229" alt="image" src="https://github.com/user-attachments/assets/398409d7-6d2b-4654-92e9-5fa1aeaa273b" />

3) Конфигурация интерфейса fa0/0 на маршрутизаторе RouterB: 

<img width="648" height="198" alt="image" src="https://github.com/user-attachments/assets/12af3b36-e523-4dec-8ae3-b89f2cc61e0b" />

4) Конфигурация интерфейса s0/3/0 на маршрутизаторах Cisco 2811: 

<img width="1345" height="280" alt="image" src="https://github.com/user-attachments/assets/4d000eef-9f59-4757-99bb-9ebad78c69d8" />

5) Создаём пулы DHCP адреса с названием Т1/T2:

<img width="1291" height="169" alt="image" src="https://github.com/user-attachments/assets/3c0324dd-2bf0-43f3-bb60-fbec8ad4b15f" />

6) Настройка протокола RIPv2 на RouterA и RouterB:

<img width="1117" height="87" alt="image" src="https://github.com/user-attachments/assets/ce08ad33-6602-4221-8478-0699b373fd79" />

7) Настройка CallManager Express на RouterA и RouterB:

<img width="1356" height="239" alt="image" src="https://github.com/user-attachments/assets/b0fa26f3-0670-48bc-afad-84014a76dfbc" />

8) Меняем имена коммутаторов

<img width="642" height="45" alt="image" src="https://github.com/user-attachments/assets/830539d1-921f-4f94-9bfa-33ade877ab64" />

9) Настраиваем порты на SwitchA и SwitchB

<img width="892" height="96" alt="image" src="https://github.com/user-attachments/assets/5a23ca0f-88e4-47ad-9baa-68709fb65cd2" />

10) Настраиваем логические линии связи, указываем номера для телефонов

<img width="1345" height="334" alt="image" src="https://github.com/user-attachments/assets/e420f102-5d75-405b-b4c1-fe7dc98d13c8" />

11) Настраиваем RouterA и RouterB для идентификации конечных точек вызова

<img width="1002" height="117" alt="image" src="https://github.com/user-attachments/assets/bb0d79a5-dd75-4e62-a4d4-379ff615ebfa" />

12) Проверка пинга

<img width="523" height="198" alt="image" src="https://github.com/user-attachments/assets/a0f62f31-a7b8-4736-9d51-9a132952f71a" />

13) Проверка вызова c телефонов

<img width="1220" height="414" alt="image" src="https://github.com/user-attachments/assets/097bc012-5ad2-420b-a0ff-3d3a9450d44f" />

#### RouterA
```

Building configuration...

Current configuration : 1230 bytes

!

version 15.1

no service timestamps log datetime msec

no service timestamps debug datetime msec

no service password-encryption

!

hostname RouterA

!

!

!

!

!

ip dhcp pool T1

 network 192.168.1.0 255.255.255.224

 default-router 192.168.1.1

 option 150 ip 192.168.1.1

!

!

!

no ip cef

no ipv6 cef

!

!

!

!

license udi pid CISCO2811/K9 sn FTX1017N21X-

!

!

!

!

!

!

!

!

!

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

 ip address 192.168.1.1 255.255.255.224

 duplex auto

 speed auto

!

interface FastEthernet0/1

 no ip address

 duplex auto

 speed auto

 shutdown

!

interface Serial0/2/0

 ip address 10.0.1.1 255.255.255.252

 clock rate 64000

!

interface Serial0/2/1

 no ip address

 clock rate 2000000

 shutdown

!

interface Vlan1

 no ip address

 shutdown

!

router rip

 version 2

 network 10.0.0.0

 network 192.168.1.0

!

ip classless

!

ip flow-export version 9

!

!

!

!

!

!

!

!

dial-peer voice 1 voip

 destination-pattern 12..

 session target ipv4:10.0.1.2

!

telephony-service

 max-ephones 5

 max-dn 5

 ip source-address 192.168.1.1 port 2000

 auto assign 4 to 6

 auto assign 1 to 5

!

ephone-dn 1

 number 1101

!

ephone-dn 2

 number 1102

!

ephone-dn 3

 number 1103

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
```
#### RouterB
```

Building configuration...

Current configuration : 1206 bytes

!

version 15.1

no service timestamps log datetime msec

no service timestamps debug datetime msec

no service password-encryption

!

hostname RouterB

!

!

!

!

!

ip dhcp pool T2

 network 172.16.1.0 255.255.255.224

 default-router 172.16.1.1

 option 150 ip 172.16.1.1

!

!

!

no ip cef

no ipv6 cef

!

!

!

!

license udi pid CISCO2811/K9 sn FTX1017S278-

!

!

!

!

!

!

!

!

!

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

 ip address 172.16.1.1 255.255.255.224

 duplex auto

 speed auto

!

interface FastEthernet0/1

 no ip address

 duplex auto

 speed auto

 shutdown

!

interface Serial0/0/0

 ip address 10.0.1.2 255.255.255.252

!

interface Serial0/0/1

 no ip address

 clock rate 2000000

 shutdown

!

interface Vlan1

 no ip address

 shutdown

!

router rip

 version 2

 network 10.0.0.0

 network 172.16.0.0

!

ip classless

!

ip flow-export version 9

!

!

!

!

!

!

!

!

dial-peer voice 1 voip

 destination-pattern 11..

 session target ipv4:10.0.1.1

!

telephony-service

 max-ephones 5

 max-dn 5

 ip source-address 172.16.1.1 port 2000

 auto assign 4 to 6

 auto assign 1 to 5

!

ephone-dn 1

 number 1201

!

ephone-dn 2

 number 1202

!

ephone-dn 3

 number 1203

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

```
#### SwitchA
```

Building configuration...

Current configuration : 1201 bytes

!

version 15.0

no service timestamps log datetime msec

no service timestamps debug datetime msec

no service password-encryption

!

hostname SwitchA

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

!

interface FastEthernet0/2

 switchport mode access

!

interface FastEthernet0/3

 switchport mode access

!

interface FastEthernet0/4

 switchport mode access

!

interface FastEthernet0/5

 switchport mode access

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

```
#### SwitchB
```

Building configuration...

Current configuration : 1206 bytes

!

version 15.1

no service timestamps log datetime msec

no service timestamps debug datetime msec

no service password-encryption

!

hostname RouterB

!

!

!

!

!

ip dhcp pool T2

 network 172.16.1.0 255.255.255.224

 default-router 172.16.1.1

 option 150 ip 172.16.1.1

!

!

!

no ip cef

no ipv6 cef

!

!

!

!

license udi pid CISCO2811/K9 sn FTX1017S278-

!

!

!

!

!

!

!

!

!

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

 ip address 172.16.1.1 255.255.255.224

 duplex auto

 speed auto

!

interface FastEthernet0/1

 no ip address

 duplex auto

 speed auto

 shutdown

!

interface Serial0/0/0

 ip address 10.0.1.2 255.255.255.252

!

interface Serial0/0/1

 no ip address

 clock rate 2000000

 shutdown

!

interface Vlan1

 no ip address

 shutdown

!

router rip

 version 2

 network 10.0.0.0

 network 172.16.0.0

!

ip classless

!

ip flow-export version 9

!

!

!

!

!

!

!

!

dial-peer voice 1 voip

 destination-pattern 11..

 session target ipv4:10.0.1.1

!

telephony-service

 max-ephones 5

 max-dn 5

 ip source-address 172.16.1.1 port 2000

 auto assign 4 to 6

 auto assign 1 to 5

!

ephone-dn 1

 number 1201

!

ephone-dn 2

 number 1202

!

ephone-dn 3

 number 1203

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
```


#### Контрольные вопросы
1. Протоколы маршрутизаций и маршрутизируемые протоколы?
Протоколы маршрутизации (RIP, OSPF, EIGRP, IGRP) служат для обмена информацией о сетях между маршрутизаторами и автоматического построения маршрутных таблиц. Маршрутизируемые протоколы (IP, IPX)-это протоколы, которые могут передаваться через сеть от узла к узлу, и для них маршрутизаторы строят маршруты.

2. Протокол RIP. Механизмы предотвращения петель маршрутизации (poisoned reverse, split horizon, hop-count limit), сравнение RIP и IGRP.
RIP использует следующие механизмы: split horizon, poisoned reverse, hop-count limit. RIP и IGRP: RIP использует метрику «количество хопов», IGRP-композитную метрику. IGRP работает только с Cisco, RIP-открытый стандарт.

3. Каким образом производится настройка DHCP-сервера на маршрутизаторе?
Создается пул DHCP командой ip dhcp pool T1, задается сеть командой network 192.168.1.0 255.255.255.224, указывается шлюз командой default-router 192.168.1.1, для голоса включается опция 150 командой option 150 ip 192.168.1.1.

4. Как работает последовательное соединение между маршрутизаторами?
Последовательное соединение используется для WAN-связей. Один маршрутизатор на стороне DCE задает тактовую частоту командой clock rate, другой на стороне DTE синхронизируется по этой частоте. Передача битов идет последовательно по одному каналу.

5. Какие скорости доступны для последовательного соединения?
Стандартные скорости: 2400, 9600, 19200, 38400, 56000, 64000, 128000, 256000, 512000, 1024000, 2048000 бит/с и выше.

6. Минимальная необходимая скорость соединения для обеспечения качества обслуживания голосового трафика.
Минимальная скорость-около 100 кбит/с на один вызов при использовании кодека G.711 (без сжатия). При использовании сжатых кодеков-около 30-40 кбит/с на вызов.

7. Как можно выйти в сеть PSTN через IP телефон?
Через шлюз VoIP, который подключается к телефонной сети общего пользования. IP-телефон звонит на номер, маршрутизатор преобразует голос в сигнал, понятный для PSTN, и передает вызов через аналоговую или цифровую линию.

8. Какой командой можно присвоить номера телефонов телефонам?
Командой number в режиме конфигурации ephone-dn.
Например:
RouterA(config)#ephone-dn 1
RouterA(config-ephone-dn)#number 1101

#### Лабораторная работа №8. Построение сети IP-телефонии между удаленными маршрутизаторами
Цель работы: изучить построение сети IP-телефонии между удаленными филиалами с помощью маршрутизаторов Cisco 2811 и Cisco 2600XM.

Создаём схему соединения:

<img width="675" height="530" alt="image" src="https://github.com/user-attachments/assets/29886a80-cda1-4611-a6d6-b3171bd65ce2" />





