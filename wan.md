#### Часть 1
Шаг 1: Построим сеть с топологией согласно схеме:
Но есть ньюанс. У стандартного маршрутизатора 2911 нет последовательных портов (Serial) по умолчанию. Их нужно добавить вручную.
Добавляем модуль HWIC-2T:

<img width="701" height="361" alt="image" src="https://github.com/user-attachments/assets/3551cfbd-b610-4ca6-bb79-d3f210ee2fdd" />

Сеть с топологией согласно схеме:

<img width="754" height="302" alt="image" src="https://github.com/user-attachments/assets/34b42f37-4c3e-41a3-89e6-03f07923996e" />

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

