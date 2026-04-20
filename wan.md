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


