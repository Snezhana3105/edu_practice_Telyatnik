#### Часть 1
Шаг 1.Построим сеть с топологией согласно схеме:

<img width="1625" height="652" alt="image" src="https://github.com/user-attachments/assets/72c8737b-75b8-4ed7-81a6-335eb99113e9" />

Шаг 2: В каждом роутере создаём Сообщение дня(MOTD) с  фио, номером группы и порядковым номером в журнале в формате:
"Работу выполнила(а) %фио% студент(ка) группы %группа%, в журнале под номером %число%"

<img width="730" height="439" alt="image" src="https://github.com/user-attachments/assets/f9bea977-0e35-4497-afcc-190add4f0fc2" />

<img width="863" height="816" alt="image" src="https://github.com/user-attachments/assets/37bccd34-421e-47d5-a960-1f75482c4543" />

<img width="862" height="849" alt="image" src="https://github.com/user-attachments/assets/51975099-9355-4bbb-9de9-f708d05e8df1" />

<img width="844" height="849" alt="image" src="https://github.com/user-attachments/assets/791db0b8-cdfd-48d3-b313-526b46f1aa2c" />

Шаг 3: Переименовываем все устройства по шаблону сокращенное название страны-сокращенное название города-роль устройства сокращенно+порядковый номер. 
Например: rus-msk-pc1.

<img width="560" height="469" alt="image" src="https://github.com/user-attachments/assets/0c108cd0-5dae-435c-bf36-56ea5dd3fe8c" />

<img width="651" height="520" alt="image" src="https://github.com/user-attachments/assets/14575cd3-a3df-491b-a8b5-05c6c76c3ece" />

<img width="729" height="539" alt="image" src="https://github.com/user-attachments/assets/7ee9891a-cc80-4100-ac4c-377c97b090d8" />

<img width="617" height="529" alt="image" src="https://github.com/user-attachments/assets/aee710f7-60cd-4d9a-93c1-047c2fd4239a" />

<img width="533" height="521" alt="image" src="https://github.com/user-attachments/assets/86f8f4f7-595f-47e2-91f2-20928036c913" />

<img width="636" height="487" alt="image" src="https://github.com/user-attachments/assets/17012921-ad0a-4b67-849e-390c8fe4fc6f" />

<img width="559" height="497" alt="image" src="https://github.com/user-attachments/assets/0d89c7f0-a05e-4d0d-90af-c63b2ea54048" />

<img width="574" height="217" alt="image" src="https://github.com/user-attachments/assets/dd84a880-ef45-47e7-86fb-2227cfabe9e7" />

<img width="525" height="270" alt="image" src="https://github.com/user-attachments/assets/6080cc94-0968-47fd-96e8-1adeaef7a5e7" />

<img width="510" height="261" alt="image" src="https://github.com/user-attachments/assets/56e9f9d6-3985-4367-8acd-6d5beee4eb42" />

<img width="581" height="329" alt="image" src="https://github.com/user-attachments/assets/ab23348b-9f9c-41d2-88b5-0a9cd6a233d0" />

<img width="526" height="279" alt="image" src="https://github.com/user-attachments/assets/c53cdae6-b4a4-4fbd-83cd-1d3157519def" />

<img width="508" height="312" alt="image" src="https://github.com/user-attachments/assets/65eb258a-c108-4610-95d4-2a7b61063de4" />

<img width="506" height="254" alt="image" src="https://github.com/user-attachments/assets/052d8c06-a373-4656-833b-c975020b921c" />

<img width="542" height="321" alt="image" src="https://github.com/user-attachments/assets/5d245c90-9fe6-4476-9c1c-8b0c496be0ff" />

<img width="486" height="331" alt="image" src="https://github.com/user-attachments/assets/2d2207e3-cd37-4598-aa67-c725b6999299" />

Шаг 4: Раздаём доменные имена согласно местоположению.
Настраиваем на всех роутерах и коммутаторах.
Для всех устройств в Новосибирске:

<img width="668" height="522" alt="image" src="https://github.com/user-attachments/assets/95109844-2706-4c25-9592-dd81a5433ce8" />

<img width="612" height="524" alt="image" src="https://github.com/user-attachments/assets/30fc33a1-b27e-4ac1-b310-77e3164d619f" />

<img width="625" height="526" alt="image" src="https://github.com/user-attachments/assets/15ed85a8-806c-448e-aa49-d3d29a68b204" />

Для всех устройств в Москве:

<img width="568" height="529" alt="image" src="https://github.com/user-attachments/assets/dc1076d2-4138-4f01-bdfd-19626a51d093" />

<img width="678" height="528" alt="image" src="https://github.com/user-attachments/assets/19c579cd-9181-436a-b0d4-24caab367284" />

<img width="580" height="528" alt="image" src="https://github.com/user-attachments/assets/8240cb29-6da8-45c4-bdbf-21f527d9e7ca" />

<img width="598" height="531" alt="image" src="https://github.com/user-attachments/assets/effde5ef-acf4-4e70-8f9e-7bad89d47ee6" />

Шаг 5. Создание VLAN на SW0 и SW1

<img width="562" height="529" alt="image" src="https://github.com/user-attachments/assets/909cc095-63ca-4bd6-a364-ea312245d32b" />

<img width="580" height="523" alt="image" src="https://github.com/user-attachments/assets/2b56dd63-46c4-433e-a80e-91f805e06cda" />

Шаг 6. Назначение портов VLAN на SW0 и SW1
<img width="636" height="605" alt="image" src="https://github.com/user-attachments/assets/102a8021-8085-4cb4-8bd1-9cedda33fbc3" />

<img width="484" height="542" alt="image" src="https://github.com/user-attachments/assets/bd219a11-6140-4cee-8049-97f174ce2805" />

Шаг 7: Создаём канал EtherChannel 2-го уровня между коммутаторами в Новосибирске, используя интерфейсы G0/1 и GO/2, со следующими требованиями:
-Используем стандартный протокол для создания логической связи под номером 1
-Коммутатор 0 является ответственным за инициирование согласования канала EtherChannel.
-Изменяем интерфейс агрегированного канала на транковый на обоих коммутаторах.
**Настройка на rus-nsk-sw0:**

<img width="802" height="615" alt="image" src="https://github.com/user-attachments/assets/a1b39b94-bdb0-4419-add0-6ae6ad239dd2" />

**Настройка на rus-nsk-sw1:**

<img width="839" height="768" alt="image" src="https://github.com/user-attachments/assets/daf62467-dc02-4115-a151-b6b0bdfbe164" />

Шаг 8. Management Interface на SW0

<img width="644" height="593" alt="image" src="https://github.com/user-attachments/assets/d9222a57-a4fd-488c-b5d1-eeccbcbc4889" />

Шаг 9. Management Interface на SW1

<img width="680" height="658" alt="image" src="https://github.com/user-attachments/assets/993e6f77-1e4c-4671-ba58-f338d43912b2" />

Шаг 10. Включение SSHv2 на SW0 и SW1
Создаем пользователя и включаем SSH:

<img width="638" height="660" alt="image" src="https://github.com/user-attachments/assets/923f0574-16a0-442c-92c6-935a20545705" />

<img width="631" height="643" alt="image" src="https://github.com/user-attachments/assets/b1c6c0a9-c7dd-45f4-b8a1-9b7abf2700ac" />

Настраиваем виртуальные линии (vty) для удаленного доступа:

<img width="635" height="645" alt="image" src="https://github.com/user-attachments/assets/79c6754e-f268-4dcb-88a6-bc7ea1d5681c" />

<img width="591" height="648" alt="image" src="https://github.com/user-attachments/assets/93b2b946-a895-48b4-8154-af2f5947d829" />

Шаг 11. Настройка транка на SW0 до R1

<img width="422" height="64" alt="image" src="https://github.com/user-attachments/assets/05f8ec1b-78ae-4496-8872-07f58bde03f5" />

Шаг 12. Настройка MOTD на SW0 и SW1

<img width="419" height="86" alt="image" src="https://github.com/user-attachments/assets/4f9e6c4f-208a-4d64-b2f5-246c7e8e06c7" />

<img width="408" height="81" alt="image" src="https://github.com/user-attachments/assets/29ad718a-ccc2-41c1-bd20-688c7bbfcf1b" />

Шаг 13. Настройка безопасности портов f0/2, f0/3, f0/4 на SW0 и SW1
SW0

<img width="634" height="277" alt="image" src="https://github.com/user-attachments/assets/6f2f8241-76ab-4a97-8cd5-b8c08bb39213" />

<img width="627" height="264" alt="image" src="https://github.com/user-attachments/assets/ea88df5c-3405-4548-adec-360f5c078db2" />

<img width="628" height="372" alt="image" src="https://github.com/user-attachments/assets/ecf6eb0a-04c1-42e7-b6da-9e98b6437ea1" />

SW1

<img width="638" height="270" alt="image" src="https://github.com/user-attachments/assets/ab832fee-77c1-4ea2-9806-743ee9b2f13a" />

<img width="623" height="277" alt="image" src="https://github.com/user-attachments/assets/9a8b2442-38d0-431e-b3d1-0f4c1b2f9d5c" />

<img width="638" height="372" alt="image" src="https://github.com/user-attachments/assets/75abf441-f75a-4b38-b8ff-5d9fae75bc12" />

Проверка после настройки
SW0

<img width="536" height="690" alt="image" src="https://github.com/user-attachments/assets/27f4eec8-7e30-41a5-8fc8-ce8809449345" />

SW1

<img width="562" height="696" alt="image" src="https://github.com/user-attachments/assets/639d8c38-8882-4280-a3c3-f8531d09bc4f" />

Шаг 14. Защита консольного подключения

<img width="325" height="87" alt="image" src="https://github.com/user-attachments/assets/f6e3a7ca-d33d-4e4e-9699-ef02b95ab71d" />

<img width="339" height="68" alt="image" src="https://github.com/user-attachments/assets/b39bef9b-926b-4793-9e04-612e54c5733c" />


Шаг 15. Отключение таймаута для консоли и SSH

<img width="382" height="115" alt="image" src="https://github.com/user-attachments/assets/1802fd9e-ee82-4bcd-9de3-98a2ef9ad2a1" />

<img width="391" height="166" alt="image" src="https://github.com/user-attachments/assets/ed41ba9b-3484-403b-882b-89faf80e93b1" />

Шаг 16. Предотвращение прерывания консоли логами

<img width="402" height="65" alt="image" src="https://github.com/user-attachments/assets/25d66cfa-125b-4845-988d-4ce28c4b0e21" />

<img width="393" height="83" alt="image" src="https://github.com/user-attachments/assets/baa9cc73-f3ad-4f40-964b-fc1a00c46c3b" />

Шаг 17. Изменение буфера истории команд

<img width="400" height="121" alt="image" src="https://github.com/user-attachments/assets/245e62dc-0ee5-4b36-92d9-1ac3fd61d689" />

<img width="375" height="128" alt="image" src="https://github.com/user-attachments/assets/cbd2bd68-834d-49ba-a9e3-395b81d94a3a" />

Сохраняем конфигурацию на SW0 и SW1 командой 
copy running-config startup-config

### Часть 2: Настройка маршрутизатора R1
 Шаг 1. Настройка интерфейса f0/1
 
<img width="616" height="187" alt="image" src="https://github.com/user-attachments/assets/2cbbdc94-03e8-487f-ab70-6f45c258510c" />

Шаг 2. Настройка маршрутизации между VLAN
1. Включим физический интерфейс, который смотрит в сторону SW0:
   
<img width="619" height="170" alt="image" src="https://github.com/user-attachments/assets/82161da9-48b3-453b-89a8-3c25bfa63e96" />

2. Создадим сабинтерфейсы для каждого VLAN. Тег должен совпадать с номером VLAN.

<img width="717" height="590" alt="image" src="https://github.com/user-attachments/assets/0987b273-09d3-4396-a8d3-54c9f85384af" />

Шаг 3. Настройка DHCP-сервера на R1
Для каждого VLAN создаем пул адресов

<img width="447" height="326" alt="image" src="https://github.com/user-attachments/assets/ef52ded2-fcd9-46ab-ba57-5f861e17cbe7" />

Исключаем адреса, которые не должны выдаваться

<img width="546" height="141" alt="image" src="https://github.com/user-attachments/assets/1a388f94-5c90-4d72-b2f5-d0ef7d92b36f" />

Проверка, что у PC0/1/2/3/4/5 выданы правильные айпи-адреса

<img width="378" height="327" alt="image" src="https://github.com/user-attachments/assets/17568df9-fe0a-4185-beea-25b6b2046fa0" />

<img width="410" height="296" alt="image" src="https://github.com/user-attachments/assets/27f91615-4799-4220-8db2-27436ddf5b50" />

<img width="370" height="315" alt="image" src="https://github.com/user-attachments/assets/96c0eb9d-ebb3-49c3-875e-d5ca287aaf7e" />

<img width="376" height="322" alt="image" src="https://github.com/user-attachments/assets/a519f3a1-a782-4b4e-a044-712aa3fdd65f" />

<img width="353" height="343" alt="image" src="https://github.com/user-attachments/assets/401e194a-1683-46cc-895b-ec59baf84650" />

<img width="341" height="345" alt="image" src="https://github.com/user-attachments/assets/9f0d3e7c-252b-4ff3-a539-5f8c5895da66" />

Шаг 4. Проверка пинга
У меня 3.0.0.100, адрес 3.0.0.101 тоже доступен, так как DHCP работает корректно.

<img width="482" height="221" alt="image" src="https://github.com/user-attachments/assets/8c7b06d0-bb50-4ca8-854d-384fb6236739" />

<img width="509" height="222" alt="image" src="https://github.com/user-attachments/assets/653a5549-cb5e-4ff7-bdfe-f417bdff96aa" />

# Часть 3

Шаг 1. Настройка имени хоста

<img width="561" height="85" alt="image" src="https://github.com/user-attachments/assets/c3100aa9-c429-4854-91a8-b608fc88ebf7" />

Шаг 2. Включение маршрутизации

<img width="273" height="17" alt="image" src="https://github.com/user-attachments/assets/b4f5268e-660f-4b21-a9ba-300dbfada967" />

Шаг 3. Создание VLAN 100 и 200 с именами

<img width="344" height="136" alt="image" src="https://github.com/user-attachments/assets/b8845275-10ff-4a94-9b4a-cdf6463b38fe" />

Проверка:

<img width="643" height="353" alt="image" src="https://github.com/user-attachments/assets/123b737f-8be9-4d27-9969-edf8b408bc3e" />

Шаг 4. Назначение портов доступа в VLAN

<img width="456" height="198" alt="image" src="https://github.com/user-attachments/assets/cc125127-291b-49b3-9805-629dd16ca43f" />

Проверка:

<img width="635" height="339" alt="image" src="https://github.com/user-attachments/assets/33039d41-b53e-445b-9c05-7ce94cb937f7" />

Шаг 5. Создание SVI для VLAN 100 и 200

<img width="628" height="291" alt="image" src="https://github.com/user-attachments/assets/baeaff76-d925-4578-9929-549e5d6a0fef" />

Проверка:

<img width="668" height="498" alt="image" src="https://github.com/user-attachments/assets/f5a2141f-6086-4c65-b3f8-4e8499dfeaf9" />

Шаг 6. Настройка интерфейсов 3-го уровня

<img width="766" height="363" alt="image" src="https://github.com/user-attachments/assets/96e4670a-daec-4559-bb93-4afc4d0a4621" />

Проверка:

<img width="694" height="404" alt="image" src="https://github.com/user-attachments/assets/9e148e8f-c737-4406-9da9-3046827eeb85" />

Шаг 7. Настройка PC6 и проверка пинга

<img width="444" height="325" alt="image" src="https://github.com/user-attachments/assets/9b7ee629-d121-45ca-9bc3-8b38bb963674" />

 Ответ от шлюза:

 <img width="488" height="281" alt="image" src="https://github.com/user-attachments/assets/67718232-bf1b-4ab5-b164-1956b902b13b" />

Также заодно настроили PC7

<img width="455" height="336" alt="image" src="https://github.com/user-attachments/assets/3cce70ed-6ba1-48cf-aa27-6c3cc4a14e53" />

Проверка:

<img width="477" height="248" alt="image" src="https://github.com/user-attachments/assets/95bc405e-ae0e-495b-9780-ac8f6ac3146e" />

