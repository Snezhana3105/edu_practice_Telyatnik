#### Часть 1
Шаг 1: Построим сеть с топологией согласно схеме:
Но есть ньюанс. У стандартного маршрутизатора 2911 нет последовательных портов (Serial) по умолчанию. Их нужно добавить вручную.
Добавляем модуль HWIC-2T:

<img width="701" height="361" alt="image" src="https://github.com/user-attachments/assets/3551cfbd-b610-4ca6-bb79-d3f210ee2fdd" />

Сеть с топологией согласно схеме:

<img width="850" height="459" alt="image" src="https://github.com/user-attachments/assets/e720643d-c463-4110-b137-507ff7a25677" />

Шаг 2: Настроим R1 по следующим условиям:
f0/0 - 10.1.1.1/24
f0/1 - 10.12.12.1/24

<img width="638" height="435" alt="image" src="https://github.com/user-attachments/assets/6553ee06-8253-4244-a84a-2535609e65b6" />

Шаг 3: Настроим R2 по следующим условиям:
f0/0 - 10.23.23.2/24
f0/1 -10.12.12.2/24

<img width="636" height="475" alt="image" src="https://github.com/user-attachments/assets/7873f481-331b-4e0d-9e2b-c323aa975e27" />

Шаг 4: Настроим R3 по следующим условиям:
loopback 3 - 3.3.3.3/8.
loopback 33 - 33.33.33.33/8.
g0/0 - 10.23.23.3/24
s0/0/0 - 30.30.30.3/24

<img width="871" height="648" alt="image" src="https://github.com/user-attachments/assets/9c921358-6fed-4ee2-b11f-1cbaaf90b09f" />

Шаг 5: Настроим R1973 по следующим условиям:
loopback 1973: IP-адрес 73.73.73.73/24
s0/0/0: IP-адрес 30.30.30.73/24

<img width="662" height="419" alt="image" src="https://github.com/user-attachments/assets/9b18e1d6-e121-47dc-808e-113bc9bc00b6" />

Проверка:

<img width="638" height="140" alt="image" src="https://github.com/user-attachments/assets/42fa06e8-fa8b-4cb2-b064-29b4be483824" />

<img width="657" height="142" alt="image" src="https://github.com/user-attachments/assets/ce15ade0-bbb7-48d6-aa4f-9751e3bdd22b" />

<img width="649" height="180" alt="image" src="https://github.com/user-attachments/assets/8aeb24df-4747-4e12-b7c0-b865b7fb1887" />

<img width="655" height="201" alt="image" src="https://github.com/user-attachments/assets/30877cf0-c66a-41f4-aede-74cfd0935a87" />

Часть 2
Перед шагами, выполним настройку тактовой частоты на DCE-порту, мы будем настраивать PPP и CHAP, нам нужно, чтобы интерфейс был полностью рабочим.
Часики на R3, поэтому выполняем команду на нём:

<img width="528" height="173" alt="image" src="https://github.com/user-attachments/assets/b0e1a431-45eb-4bf3-bd1c-8db58c7d36b2" />


Используемый пароль: CiscoCHAP
Шаг 1: Настроим последовательные интерфейсы между R3 и R1973 с использованием PPP и мы должны убедиться, что оба маршрутизатора аутентифицируют
друг друга с использованием максимально надежного протокола аутентификации.
Настройка R3 - создаём пользователя и включаем PPP CHAP:

<img width="651" height="276" alt="image" src="https://github.com/user-attachments/assets/37a0e087-97d5-48a0-b2f1-d45d5718e2d7" />

Настройка R1973 - создаём пользователя и включаем PPP CHAP:

<img width="640" height="215" alt="image" src="https://github.com/user-attachments/assets/233f7246-a518-44ac-9cbd-896f969deee2" />

Проверка:

<img width="604" height="446" alt="image" src="https://github.com/user-attachments/assets/543ea156-10e4-4eb9-bff8-340f30040f72" />

#### Часть 3
Шаг 1: Настроим OSPFv2 на маршрутизаторах R1, R2 и R3 - Выполним его по частям в следующих шагах.
Шаг 2: Настроим маршрутизатор R2 так, чтобы он использовал ID маршрутизатора 0.0.0.2.

<img width="568" height="118" alt="image" src="https://github.com/user-attachments/assets/9380252b-4cdf-4c64-95a6-4f2b6448bc7c" />


Шаг 3: Настроим маршрутизаторы R1, R2 и R3 так, чтобы они объявляли все свои подключенные сети в OSPF.
R1:

<img width="550" height="170" alt="image" src="https://github.com/user-attachments/assets/6ff8c565-79a1-4baa-8406-07d7a4f1357e" />


R2:

<img width="501" height="93" alt="image" src="https://github.com/user-attachments/assets/e23e67e8-acbe-4d81-8299-36f287361bc8" />


R3:

<img width="558" height="185" alt="image" src="https://github.com/user-attachments/assets/c076c8f4-1af6-4583-85b0-4417d42083af" />


Шаг 4: Используем ID процесса 100 для OSPF на всех маршрутизаторах (R1, R2 и R3). - Уже сделали в шагах 2-3 (везде router ospf 100)
Шаг 5: Настроим интерфейс f0/0 маршрутизатора R1 так, чтобы он принадлежал зоне 1 - Уже сделали это в шаге 3 для R1 (network 10.1.1.0 0.0.0.255 area 1)
Шаг 6: Настроим интерфейс f0/1 маршрутизатора R1 так, чтобы он принадлежал зоне 0 -  Уже сделали это в шаге 3 для R1 (network 10.12.12.0 0.0.0.255 area 0)
Шаг 7: Настроим интерфейс f0/0 маршрутизатора R2 так, чтобы он принадлежал зоне 23 -  Уже сделали это в шаге 3 для R2 (network 10.23.23.0 0.0.0.255 area 23)
Шаг 8: Настроим интерфейс f0/1 маршрутизатора R2 так, чтобы он принадлежал зоне 0 - Уже сделали это в шаге 3 для R2 (network 10.12.12.0 0.0.0.255 area 0)
Шаг 9: Настроим интерфейс f0/0, интерфейс loopback3 и loopback33 маршрутизатора R3 так, чтобы они принадлежали зоне 23 - Уже сделали это в шаге 3 для R3 (все три сети в зоне 23)

Шаг 10: Заблокируем отправку hello-пакетов OSPF на всех интерфейсах маршрутизатора R1, кроме интерфейса f0/1.

<img width="637" height="221" alt="image" src="https://github.com/user-attachments/assets/63024c5f-ff7d-40d3-9452-b8270ef6a072" />


Шаг 11: Настроим маршрутизатор R2 так, чтобы он всегда был назначенным маршрутизатором (DR) на всех многодоступовых сетях (broadcast и NBMA).
Блок команд (для f0/0):

<img width="334" height="66" alt="image" src="https://github.com/user-attachments/assets/8ffa2f8d-bd60-441b-9b29-b3443247ab6e" />


Блок команд (для f0/1):

<img width="478" height="134" alt="image" src="https://github.com/user-attachments/assets/df72aa0e-34e7-4999-b8b8-ea2e060a52ae" />

Шаг 12: Настроим маршрутизатор R3 так, чтобы он работал в качестве шлюза по умолчанию для всех маршрутизаторов OSPF, чтобы они могли взаимодействовать с любыми другими сетями. В R3 будет команда default-information originate

<img width="596" height="208" alt="image" src="https://github.com/user-attachments/assets/23c8d571-1cfe-458e-8c4f-4c4b41c49e26" />

Проверка:
1. Соседства OSPF

<img width="652" height="180" alt="image" src="https://github.com/user-attachments/assets/849b3436-fcd4-47d5-ab41-6a51ee7c6699" />


2. Маршруты OSPF в таблице маршрутизации

<img width="591" height="187" alt="image" src="https://github.com/user-attachments/assets/5ea817de-d591-4f62-8002-2c21d9ea0576" />


3. Маршрут по умолчанию (шлюз)

<img width="561" height="107" alt="image" src="https://github.com/user-attachments/assets/90af03a3-67be-4a6f-8536-cb90687b2bec" />


#### Часть 4
Шаг 1: Настроим BGP между R3 и R1973 - Выполним по шагам ниже.
Шаг 2: Укажем, что все маршрутизаторы, использующие протокол OSPF, находятся в автономной системе BGP (AS) номер 3
Запускаем процесс BGP на R3 и указываем, что он находится в автономной системе (AS) номер 3. В эту же AS попадают все роутеры с OSPF (R1, R2, R3).

<img width="545" height="134" alt="image" src="https://github.com/user-attachments/assets/f9b81400-cf60-49ee-8147-3337060ef6f6" />


Шаг 3: Маршрутизатор R1973 находится в автономной системе BGP (AS) номер 1973

<img width="555" height="164" alt="image" src="https://github.com/user-attachments/assets/c1ed28f4-4b16-4fce-80ad-35c9dd3fe971" />

R1973 находится в отдельной AS - номер 1973. Это будет внешнее BGP-соседство, так как AS разные (3 и 1973).
Шаг 4: Настроим маршрутизатор R3 для установления внешнего BGP-соседства с маршрутизатором R1973.

<img width="536" height="133" alt="image" src="https://github.com/user-attachments/assets/e16ef61a-7ba8-41e3-891f-98a338a5bb74" />


Шаг 5: Настроим маршрутизатор R1973 так, чтобы он объявил свой loopback- интерфейс маршрутизатору R3.

<img width="588" height="166" alt="image" src="https://github.com/user-attachments/assets/09fff9e4-a857-41ab-b742-94bc3f0479c1" />


Шаг 6: Настроим маршрутизатор R1973 так, чтобы маршрут по умолчанию указывал на маршрутизатор R3.

<img width="530" height="138" alt="image" src="https://github.com/user-attachments/assets/872b2c87-0821-4e78-be4c-949f25a4fe32" />

Проверка:
1. BGP-соседство

<img width="639" height="281" alt="image" src="https://github.com/user-attachments/assets/0d8ed2d4-810e-4466-9bb4-3fb1e23a2318" />


2. Какие маршруты получил R3 через BGP

<img width="602" height="179" alt="image" src="https://github.com/user-attachments/assets/e8b14a6c-856f-4f3c-91f0-f28e871c0997" />


3. Маршрут по умолчанию на R1973

<img width="548" height="89" alt="image" src="https://github.com/user-attachments/assets/d6a1bd54-6e7e-4497-8b69-79485cc912ef" />

#### Часть 5
Шаг 1: Убедимся, что IOS на R3 поддерживает все команды VOIP и расширенные настройки безопасности, используя для этого оценочную лицензию.

<img width="907" height="540" alt="image" src="https://github.com/user-attachments/assets/9516c74a-ce46-488c-800e-36aa10e09b0b" />

<img width="555" height="384" alt="image" src="https://github.com/user-attachments/assets/70ea5edf-5f18-4ed2-9b25-ba255cf1352d" />

Шаг 2: Установим лицензии UCK9

<img width="551" height="112" alt="image" src="https://github.com/user-attachments/assets/d0a40785-0b23-4347-bf05-86e6f8218810" />

Шаг 3: Установим лицензии securityk9

<img width="1202" height="721" alt="image" src="https://github.com/user-attachments/assets/cd7435d2-4ada-4e77-8a23-60e41c85bb6d" />

Шаг 4: Сохраним конфигурацию

<img width="448" height="142" alt="image" src="https://github.com/user-attachments/assets/411d3be9-6de3-4c60-ad2c-44cb9ae877c4" />

Шаг 5: Перезагрузим маршрутизатор
команда: license boot module _серия роутера_ technology-package _лицензия_

<img width="693" height="337" alt="image" src="https://github.com/user-attachments/assets/4ca26ce3-a088-4ecd-b9a1-5883d02b0cc2" />

Проверка:

<img width="916" height="222" alt="image" src="https://github.com/user-attachments/assets/6c3cfd0d-5357-4159-8a43-5b0b6033901c" />

#### Часть 6
Шаг 1: Настроим R1 в качестве DHCP-ретранслятора
Шаг 1.1: Убедимся, что DHCP-сервер уже есть на схеме

<img width="484" height="343" alt="image" src="https://github.com/user-attachments/assets/0cd06fed-2dde-4863-8741-03cdf8c9c0d6" />

Шаг 1.2: Настройка IP-адреса на DHCP-сервере

<img width="432" height="302" alt="image" src="https://github.com/user-attachments/assets/4cbbb8b5-1e38-4cfe-9eaf-03e99e479ac0" />

Шаг 1.3: Настройка DHCP-пула на сервере

<img width="525" height="527" alt="image" src="https://github.com/user-attachments/assets/e90c6784-b629-4639-8f4a-123f81963a1d" />

Шаг 1.4: Настройка DHCP-ретранслятора на R1

<img width="581" height="154" alt="image" src="https://github.com/user-attachments/assets/6643ffc2-df5c-4f76-bc34-b9aeab77bab6" />

Команда ip helper-address 10.23.23.100 заставляет R1 пересылать широковещательные DHCP-запросы на указанный IP-адрес DHCP-сервера.
Шаг 2: Убедимся, что PC0 может получить IPv4 от DHCP-сервера с IP 10.23.23.100.
Проблема: R2 и R3 в одной зоне 23, но R2 не отправляет summary-маршруты. У меня из за этого не правильный IP-адресс был.
Решение: clear ip ospf process - перезапускаем OSPF на R2

<img width="372" height="225" alt="image" src="https://github.com/user-attachments/assets/4326fe10-70e0-4751-ad73-eb3552f557ea" />

#### Часть 7:
Шаг 1: Настроим маршрутизаторы R1, R2, R3, R1973 с IPv6-адресами
Шаг 1.1: Включение IPv6-маршрутизации на всех роутерах

<img width="532" height="158" alt="image" src="https://github.com/user-attachments/assets/5fd56a00-7a0b-4718-97b5-4cd4ce615f34" />

<img width="576" height="152" alt="image" src="https://github.com/user-attachments/assets/e03a62b8-0f58-4ec6-8702-852cef90d131" />

<img width="560" height="116" alt="image" src="https://github.com/user-attachments/assets/67d927a4-2d01-42bf-b8f8-5d98e5ea9bbe" />

<img width="529" height="157" alt="image" src="https://github.com/user-attachments/assets/ce142eca-a5f7-4427-8799-1ae5b462ba70" />

Шаг 1.2: Настройка R1

<img width="557" height="229" alt="image" src="https://github.com/user-attachments/assets/4bb649d3-ffbe-4a63-abf7-f2005a44a3d5" />

Шаг 1.3: Настройка R2

<img width="550" height="214" alt="image" src="https://github.com/user-attachments/assets/4e5e7360-c583-4198-a897-09aabf9c985c" />

Шаг 1.4: Настройка R3

<img width="537" height="213" alt="image" src="https://github.com/user-attachments/assets/b1d249e0-5e1c-4dc3-852d-d08c78261cdd" />

Шаг 1.5: Настройка R1973

<img width="536" height="212" alt="image" src="https://github.com/user-attachments/assets/50797431-9b5c-4c50-904c-ab20ea6ddc05" />

Шаг 2: Убедимся, что на всех маршрутизаторах включена возможность маршрутизации IPv6. - Уже сделали это в Шаге 1.1 (ipv6 unicast-routing).
Проверка:

<img width="427" height="59" alt="image" src="https://github.com/user-attachments/assets/70ac7c48-3588-4fe4-b701-f70cb4611413" />

Шаг 3: Убедимся, что интерфейс f0/0 на маршрутизаторе R1 использует локальный
адрес канала fe80::1.

<img width="517" height="382" alt="image" src="https://github.com/user-attachments/assets/e7fd71e4-5226-446b-8814-7e06ae6b2ac6" />

Шаг 4: Убедимся, что R1 использует функцию EUI-64 для своего глобального адреса
на интерфейсе f0/0.

<img width="527" height="431" alt="image" src="https://github.com/user-attachments/assets/b59d7a38-dd37-4919-9809-ef26516ffc6e" />

Дополнительная проверка: Маршрут по умолчанию IPv6 на R3
По заданию из файла ipv6.txt, на R3 нужно добавить маршрут по умолчанию:

<img width="536" height="123" alt="image" src="https://github.com/user-attachments/assets/2772f09c-1183-4412-abd3-97d1534a635a" />

Проверка:

<img width="655" height="374" alt="image" src="https://github.com/user-attachments/assets/7c3b9abb-3f3b-4121-92fd-432274ff729a" />

#### Часть 8
Шаг 1: Настроим OSPFv3 между R1, R2 и R3 - Выполним в следующих шагах.
Шаг 2: R1 будет использовать router-id 0.0.0.1, R2 будет использовать router-id 0.0.0.2, R3 будет использовать router-id 0.0.0.3
Настройка R1:

<img width="532" height="134" alt="image" src="https://github.com/user-attachments/assets/11ed0fc4-1e3a-41db-be53-9a063be85021" />

Настройка R2:

<img width="576" height="130" alt="image" src="https://github.com/user-attachments/assets/56760c24-a55a-4169-9f6c-67fdfc85c566" />

Настройка R3:

<img width="584" height="170" alt="image" src="https://github.com/user-attachments/assets/68d61afd-9a36-4d2b-9350-0aa4cbbd08b3" />

Шаг 3: R1, R2 и R3 должны объявлять все подключенные сети IPv6.
Настройка R1:

<img width="459" height="167" alt="image" src="https://github.com/user-attachments/assets/48c3e1b5-5e42-4369-a951-396a85ff24ea" />

Настройка R2:

<img width="447" height="172" alt="image" src="https://github.com/user-attachments/assets/c5258f83-df6e-4498-85fd-5b38bcc7c3f0" />

Настройка R3:

<img width="464" height="99" alt="image" src="https://github.com/user-attachments/assets/995fc3a2-a537-4389-ae9b-044970b89edc" />

Шаг 4: Используем номер процесса 100 для всех маршрутизаторов.  - Уже сделали это в шаге 2 (везде ipv6 router ospf 100)
Шаг 5: Интерфейс f0/0 маршрутизатора R1 будет подключен к Area 1, интерфейс f0/1 маршрутизатора R1 будет подключен к Area 0  - Уже сделали это в шаге 3 для R1. 
Шаг 6: Интерфейс f0/0 маршрутизатора R2 будет подключен к Area 23, интерфейс f0/1 маршрутизатора R2 будет подключен к Area 0 - Уже сделали это в шаге 3 для R2. 
Шаг 7: Интерфейс g0/0 маршрутизатора R3 будет подключен к Area 23 - Уже сделали это в шаге 3 для R3. 
Шаг 8: R1 не должен отправлять hello-сообщения из всех своих текущих и будущих добавленных интерфейсов, кроме f0/1.

<img width="642" height="194" alt="image" src="https://github.com/user-attachments/assets/0c6f280b-d5e2-4d1e-b32a-e9b886c6ed92" />


Шаг 9: Настроим R3 для работы в качестве шлюза по умолчанию для всех маршрутизаторов OSPF для связи с любыми другими сетями.

<img width="560" height="133" alt="image" src="https://github.com/user-attachments/assets/fdacb0c3-2ae6-4347-952d-7b724e28322a" />

Проверка OSPFv3:
1. Соседства OSPFv3

<img width="651" height="148" alt="image" src="https://github.com/user-attachments/assets/6d9e8cd4-5872-4018-8813-13a02286a4d0" />

2. Маршруты OSPFv3 в таблице IPv6 маршрутизации

<img width="628" height="228" alt="image" src="https://github.com/user-attachments/assets/73490c07-129c-4758-aaa1-567339e32348" />

Часть 9
Шаг 1: Настройте EIGRPv6 между R3 и R1973. - Выполним в следующих шагах.
Шаг 2: Укажите номер автономной системы (AS) 100
Настройка R3:

<img width="543" height="94" alt="image" src="https://github.com/user-attachments/assets/c1553a01-d9e9-43eb-91c8-004f92b6f86b" />

Настройка R1973:

<img width="567" height="101" alt="image" src="https://github.com/user-attachments/assets/e985ec5f-4514-44d6-b0cc-f24691678c86" />

Шаг 3: R3 должен использовать router-id 0.0.0.3, R1973 будет использовать router-id 0.0.0.73.
Настройка R3:

<img width="548" height="134" alt="image" src="https://github.com/user-attachments/assets/c23ac73c-0fd4-4010-89c5-c24c1b44b07a" />

На R1973:

<img width="360" height="66" alt="image" src="https://github.com/user-attachments/assets/ab191bf9-c0b7-41d3-b8b7-9411fadfb980" />

Проверка:
1. Состояние интерфейсов EIGRPv6

<img width="670" height="162" alt="image" src="https://github.com/user-attachments/assets/01c602d8-fab6-41c5-b3ed-a851a18566ed" />

2. Соседи EIGRPv6

<img width="653" height="176" alt="image" src="https://github.com/user-attachments/assets/8a2b2f23-9fe5-43f8-959e-d2104dfa2cc7" />

3.Маршруты EIGRPv6 на R3

<img width="671" height="156" alt="image" src="https://github.com/user-attachments/assets/4c6ee3a0-0593-4b5e-a39a-81bf4ed70ecd" />

Шаг 4: R1973 должен объявить свою петлевую сеть (loopback) для R3 через EIGRPv6.

<img width="693" height="150" alt="image" src="https://github.com/user-attachments/assets/70b48930-c00f-4782-aefd-8843fbce1e38" />

Шаг 5: Настройте на R1973 маршрут по умолчанию IPv6, указывающий на R3 в качестве следующего хопа (next hop) для связи с любыми другими сетями.

<img width="658" height="130" alt="image" src="https://github.com/user-attachments/assets/cdac7ad3-d0d2-4c31-a7ad-fa43e9214623" />

Без команды "no shutdown" EIGRPv6 не будет должным образом работать и
функционировать.

```
R1  
enable  
conf t  
hostname R1  
interface fastEthernet 0/0  
ip address 10.1.1.1 255.255.255.0  
no shutdown  
exit  
interface fastEthernet 0/1  
ip address 10.12.12.1 255.255.255.0  
no shutdown  
end  
conf t  
router ospf 100  
network 10.1.1.0 0.0.0.255 area 1  
network 10.12.12.0 0.0.0.255 area 0  
passive-interface default  
no passive-interface fastEthernet 0/1  
end  
conf t  
interface fastEthernet 0/0  
ip helper-address 10.23.23.100  
end  
conf t  
ipv6 unicast-routing  
interface fastEthernet 0/0  
ipv6 address fe80::1 link-local  
ipv6 address 2001:10:10:10::/64 eui-64  
no shutdown  
exit  
interface fastEthernet 0/1  
ipv6 address 2001:11:11:11::1/64  
no shutdown  
end  
conf t  
ipv6 router ospf 100  
router-id 0.0.0.1  
passive-interface default  
no passive-interface fastEthernet 0/1  
exit  
interface fastEthernet 0/0  
ipv6 ospf 100 area 1  
exit  
interface fastEthernet 0/1  
ipv6 ospf 100 area 0  
end  
write memory  
```


```
R2  
enable  
conf t  
hostname R2  
interface fastEthernet 0/0  
ip address 10.23.23.2 255.255.255.0  
no shutdown  
exit  
interface fastEthernet 0/1  
ip address 10.12.12.2 255.255.255.0  
no shutdown  
end  
conf t  
router ospf 100  
router-id 0.0.0.2  
network 10.12.12.0 0.0.0.255 area 0  
network 10.23.23.0 0.0.0.255 area 23  
exit  
interface fastEthernet 0/0  
ip ospf priority 255  
exit  
interface fastEthernet 0/1  
ip ospf priority 255  
end  
conf t  
ipv6 unicast-routing  
interface fastEthernet 0/0  
ipv6 address 2001:12:12:12::2/64  
no shutdown  
exit  
interface fastEthernet 0/1  
ipv6 address 2001:11:11:11::2/64  
no shutdown  
end  
conf t  
ipv6 router ospf 100  
router-id 0.0.0.2  
exit  
interface fastEthernet 0/0  
ipv6 ospf 100 area 23  
exit  
interface fastEthernet 0/1  
ipv6 ospf 100 area 0  
end  
write memory  
```

```
R2  
enable  
conf t  
hostname R2  
interface fastEthernet 0/0  
ip address 10.23.23.2 255.255.255.0  
no shutdown  
exit  
interface fastEthernet 0/1  
ip address 10.12.12.2 255.255.255.0  
no shutdown  
end  
conf t  
router ospf 100  
router-id 0.0.0.2  
network 10.12.12.0 0.0.0.255 area 0  
network 10.23.23.0 0.0.0.255 area 23  
exit  
interface fastEthernet 0/0  
ip ospf priority 255  
exit  
interface fastEthernet 0/1  
ip ospf priority 255  
end  
conf t  
ipv6 unicast-routing  
interface fastEthernet 0/0  
ipv6 address 2001:12:12:12::2/64  
no shutdown  
exit  
interface fastEthernet 0/1  
ipv6 address 2001:11:11:11::2/64  
no shutdown  
end  
conf t  
ipv6 router ospf 100  
router-id 0.0.0.2  
exit  
interface fastEthernet 0/0  
ipv6 ospf 100 area 23  
exit  
interface fastEthernet 0/1  
ipv6 ospf 100 area 0  
end  
write memory 
```


```
R3  
enable  
conf t  
hostname R3  
interface loopback 3  
ip address 3.3.3.3 255.0.0.0  
exit  
interface loopback 33  
ip address 33.33.33.33 255.0.0.0  
exit  
interface gigabitEthernet 0/0  
ip address 10.23.23.3 255.255.255.0  
no shutdown  
exit  
interface serial 0/3/0  
ip address 30.30.30.3 255.255.255.0  
no shutdown  
end  
conf t  
username R1973 password CiscoCHAP  
interface serial 0/3/0  
encapsulation ppp  
ppp authentication chap  
clock rate 64000  
end  
conf t  
router ospf 100  
network 10.23.23.0 0.0.0.255 area 23  
network 3.3.3.0 0.0.0.255 area 23  
network 33.33.33.0 0.0.0.255 area 23  
default-information originate  
end  
conf t  
router bgp 3  
neighbor 30.30.30.73 remote-as 1973  
end  
conf t  
license boot module c2900 technology-package uck9  
yes  
license boot module c2900 technology-package securityk9  
yes  
end  
copy running-config startup-config  
reload  
conf t  
ipv6 unicast-routing  
interface gigabitEthernet 0/0  
ipv6 address 2001:12:12:12::3/64  
no shutdown  
exit  
interface serial 0/3/0  
ipv6 address 2001:30:30:30::3/64  
no shutdown  
end  
conf t  
ipv6 route ::/0 2001:30:30:30::1973  
end  
conf t  
ipv6 router ospf 100  
router-id 0.0.0.3  
default-information originate  
exit  
interface gigabitEthernet 0/0  
ipv6 ospf 100 area 23  
end  
conf t  
ipv6 router eigrp 100  
no shutdown  
exit  
interface serial 0/3/0  
ipv6 eigrp 100  
no shutdown  
end  
write memory  
```



```
R1973  
enable  
conf t  
hostname R1973  
interface loopback 1973  
ip address 73.73.73.73 255.255.255.0  
exit  
interface serial 0/3/0  
ip address 30.30.30.73 255.255.255.0  
no shutdown  
end  
conf t  
username R3 password CiscoCHAP  
interface serial 0/3/0  
encapsulation ppp  
ppp authentication chap  
end  
conf t  
router bgp 1973  
neighbor 30.30.30.3 remote-as 3  
network 73.73.73.0 mask 255.255.255.0  
exit  
ip route 0.0.0.0 0.0.0.0 30.30.30.3  
end  
conf t  
ipv6 unicast-routing  
interface loopback 1973  
ipv6 address 2001:1973:1973:1973::1973/64  
no shutdown  
exit  
interface serial 0/3/0  
ipv6 address 2001:30:30:30::1973/64  
no shutdown  
end  
conf t  
ipv6 router eigrp 100  
no shutdown  
exit  
interface serial 0/3/0  
ipv6 eigrp 100  
no shutdown  
exit  
interface loopback 1973  
ipv6 eigrp 100  
no shutdown  
end  
conf t  
ipv6 route ::/0 2001:30:30:30::3  
end  
write memory  
```
