#### Часть 1
Шаг 1.Построим сеть с топологией согласно схеме:

<img width="1625" height="652" alt="image" src="https://github.com/user-attachments/assets/72c8737b-75b8-4ed7-81a6-335eb99113e9" />

****
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

# Часть 4
Шаг 1. Настройка IP-адресов на R2

<img width="798" height="454" alt="image" src="https://github.com/user-attachments/assets/6c672f67-5bd2-41de-8118-035ee50fa175" />

Проверка:

<img width="714" height="90" alt="image" src="https://github.com/user-attachments/assets/b1ddd92c-53b8-4048-a074-bbf50d203779" />

Шаг 2. Настройка IP-адресов на R3

<img width="707" height="457" alt="image" src="https://github.com/user-attachments/assets/89c60da2-8808-4cd0-a534-ed114d9c9ff1" />

Проверка:

<img width="683" height="112" alt="Pasted_image_20260415164633" src="https://github.com/user-attachments/assets/e1cd145a-7d8c-44da-a7fa-d356203c22cd" />

Шаг 3: Настройка HSRP на R2 и R3:

<img width="546" height="244" alt="Pasted_image_20260415165036" src="https://github.com/user-attachments/assets/33ede68d-36c1-431f-8e8f-7facd3ec71a0" />

<img width="545" height="195" alt="Pasted_image_20260415165054" src="https://github.com/user-attachments/assets/7d3b54ed-771f-49e7-a307-f65d742ef276" />

Проверка HSRP:

<img width="548" height="241" alt="Pasted_image_20260415165133" src="https://github.com/user-attachments/assets/abb8b4f7-dc79-41c5-8b90-7d1157c50e93" />

<img width="582" height="252" alt="Pasted_image_20260415165310" src="https://github.com/user-attachments/assets/3ef75e08-f9e7-442d-84f7-fbdee66fa8fa" />

Проверка связности между R2 и R3:

<img width="579" height="135" alt="Pasted_image_20260415165446" src="https://github.com/user-attachments/assets/176245ca-d675-425e-adf4-c7a86e2cf835" />

<img width="592" height="134" alt="Pasted_image_20260415165530" src="https://github.com/user-attachments/assets/04776fd0-6cc7-4d35-8b32-8003f2623510" />

Проверка связности с MLS:

<img width="644" height="64" alt="Pasted_image_20260415165619" src="https://github.com/user-attachments/assets/850cc98a-df62-4741-8b78-73458a0f4031" />

Настройка Server0(на всякий случай):

<img width="353" height="303" alt="Pasted_image_20260415165740" src="https://github.com/user-attachments/assets/e229826c-6acb-44be-9ec6-65f3e7a46f8f" />

Сервер использует виртуальный шлюз 10.0.0.1. Если R2 упадёт, R3 автоматически подхватит этот айпи, и сервер не заметит сбоя.
Проверка связности с сервера:

<img width="491" height="680" alt="Pasted_image_20260415170000" src="https://github.com/user-attachments/assets/762485a9-03c7-409c-b39b-46bd96d3e4b9" />

# Часть 5
Шаг 1: Настройка EIGRP на R1,R2,R3,MLS

<img width="586" height="311" alt="Pasted_image_20260415171104" src="https://github.com/user-attachments/assets/af3f7615-8737-4f1c-be02-72f944724c6f" />

<img width="547" height="246" alt="image" src="https://github.com/user-attachments/assets/70eb8118-0043-4342-b895-0668fac42ced" />

<img width="628" height="310" alt="image" src="https://github.com/user-attachments/assets/b4ee847e-a468-4196-9d4c-abfd211a3c38" />

<img width="646" height="443" alt="image" src="https://github.com/user-attachments/assets/fbfd93b7-6a44-4ee3-be8b-ddca925b705a" />

Шаг 2. Проверка соседства EIGRP
<img width="636" height="131" alt="image" src="https://github.com/user-attachments/assets/aff6edec-2f68-44fd-8240-1641027964aa" />

<img width="620" height="150" alt="image" src="https://github.com/user-attachments/assets/942ea1be-c7d7-425b-9bff-215c0e332a23" />

<img width="611" height="182" alt="image" src="https://github.com/user-attachments/assets/73f10585-c302-4b7c-b618-3ae98a712d7a" />

<img width="616" height="159" alt="image" src="https://github.com/user-attachments/assets/4109f0f9-6271-4f50-97df-103556dc648e" />

Проверка таблицы маршрутизации:

<img width="628" height="177" alt="image" src="https://github.com/user-attachments/assets/69f048b4-836e-414b-aded-56658efaa9de" />

Пинг с сервера:

<img width="463" height="236" alt="image" src="https://github.com/user-attachments/assets/ce3ef3fc-f581-4b56-9cfd-4ab70f090726" />

<img width="469" height="217" alt="image" src="https://github.com/user-attachments/assets/90393751-c438-4f8b-be7a-02f5373ab2b9" />

<img width="462" height="218" alt="image" src="https://github.com/user-attachments/assets/8af63b16-d2bd-404b-ad30-cfa5608ce570" />

#### Часть 6
Шаг 1. Пропинговать с Server0 (10.0.0.100) ПК в VLAN 2 (2.0.0.100)

<img width="474" height="234" alt="image" src="https://github.com/user-attachments/assets/15deb6db-9f96-47b0-822a-2fabd8c4517a" />

Шаг 2. Настроить ACL на SW1, чтобы **только** ПК 2.0.0.100 имел доступ к веб-серверу 10.0.0.100.
Убедимся, что веб-сервер работает на Server0

<img width="390" height="229" alt="image" src="https://github.com/user-attachments/assets/e21c738f-0255-4aee-b2d0-0bd03a970eb7" />

<img width="605" height="227" alt="image" src="https://github.com/user-attachments/assets/f798df70-c53a-4780-b9ef-1564c7d90b91" />

Шаг 3. Ограничение SSH на SW1

<img width="629" height="220" alt="image" src="https://github.com/user-attachments/assets/34cc2d0e-7806-4e8e-ae71-d62866dea16e" />

Проверка:

<img width="1389" height="409" alt="image" src="https://github.com/user-attachments/assets/7346de89-fe0d-4ef0-92dd-b06dfc8bb27f" />

#### Часть 7
Шаг 1. Создание loopback-интерфейса на R1

<img width="639" height="340" alt="image" src="https://github.com/user-attachments/assets/2d771229-e9fd-46d2-adc6-6b1f464796fe" />

Проверка:

<img width="625" height="58" alt="image" src="https://github.com/user-attachments/assets/a71047d3-c9a0-4719-8b85-a118baab51bf" />

Шаг 2. Создание loopback-интерфейса на R3

<img width="641" height="327" alt="image" src="https://github.com/user-attachments/assets/1fecf02f-625e-4ef5-b49e-b3bff7473174" />

Проверка:

<img width="636" height="76" alt="image" src="https://github.com/user-attachments/assets/ae2f3a39-dcd8-4fdb-bb1e-805d23c0ec4a" />

Шаг 3. R1 и R3 объявляют loopback-интерфейсы друг другу, используя RIPv2.
На R1:

<img width="557" height="222" alt="image" src="https://github.com/user-attachments/assets/f562576f-7422-46cc-96ae-f3d85f0cb5cb" />

На R3:

<img width="566" height="237" alt="image" src="https://github.com/user-attachments/assets/a5eacb05-fa65-4a3e-87a6-cfcd561f8d2b" />

Шаг 4. Проверка, что RIPv2 работает ТОЛЬКО на R1 и R3
Должно быть пусто:

<img width="1381" height="681" alt="image" src="https://github.com/user-attachments/assets/9c54ab41-32ee-4d13-8593-c8f08826329a" />

RIPv2 работает ТОЛЬКО на R1 и R3:

<img width="511" height="120" alt="image" src="https://github.com/user-attachments/assets/4814b775-19c0-41e4-a7ec-546e538e825e" />

<img width="501" height="105" alt="image" src="https://github.com/user-attachments/assets/11e8c825-a566-4a34-9f09-6ed111c82a57" />

Шаг 5: IP-адреса при использовании туннелей должны быть 200.200.200.#/24, где # - это ID маршрутизатора.
Создание туннеля между R1 и R3
Узнаём IP-адрес интерфейса, который смотрит в сторону Москвы (Fa0/1):

<img width="625" height="68" alt="image" src="https://github.com/user-attachments/assets/2699c739-723a-43c1-b56d-30c6393cafab" />

Теперь создаём туннель:

<img width="642" height="290" alt="image" src="https://github.com/user-attachments/assets/8d977c58-2d36-4d7f-8c4b-f5436116d154" />

На R3:
Узнаём IP-адрес интерфейса, который смотрит в сторону MLS (Fa0/1):

<img width="605" height="56" alt="image" src="https://github.com/user-attachments/assets/02c05dc1-8eb6-4e8a-a0e4-560ff6f65ce0" />

Теперь создаём туннель:

<img width="621" height="282" alt="image" src="https://github.com/user-attachments/assets/48c0a0e1-7276-4b65-a542-e8477e8f39c0" />

Проверка туннеля

<img width="1372" height="671" alt="image" src="https://github.com/user-attachments/assets/bc06cc99-ac9c-4ed4-89cd-920cd7618f7b" />

Проверка связности через туннель:

<img width="631" height="158" alt="image" src="https://github.com/user-attachments/assets/2a52efb1-a388-4658-99ed-2071d6d097fe" />

<img width="606" height="158" alt="image" src="https://github.com/user-attachments/assets/3026e905-ce4b-4cc2-a7c6-945e704142bd" />

Проверка RIPv2 и маршрутов

<img width="582" height="80" alt="image" src="https://github.com/user-attachments/assets/7d03ddd0-1b92-4ab2-b649-28ccd1d0f44b" />

<img width="588" height="111" alt="image" src="https://github.com/user-attachments/assets/5fbd3af9-2bec-4597-9504-f69b69622999" />

Шаг 6. Расширенный ping для проверки

<img width="629" height="326" alt="image" src="https://github.com/user-attachments/assets/ab705c44-b07b-4384-869e-f38c66e06c5d" />

#### Часть 8
Шаг 1: Настройка NTP и Syslog на R1, R2, R3, MLS
1.1: Настройка Server0 как NTP-сервера

<img width="699" height="627" alt="image" src="https://github.com/user-attachments/assets/278f271c-6919-4250-8e99-899d916bab0b" />

1.2: Настройка NTP-клиента на R1

<img width="510" height="136" alt="image" src="https://github.com/user-attachments/assets/1a4d2da9-9e58-4b9f-b2b4-e2d39dcb3311" />

1.3: Настройка NTP-клиента на R2

<img width="537" height="294" alt="image" src="https://github.com/user-attachments/assets/45fdbc1a-52d7-4552-b6cc-5e79e7584fcf" />

1.4: Настройка NTP-клиента на R3

<img width="546" height="285" alt="image" src="https://github.com/user-attachments/assets/83fdffed-abfe-44fe-af08-324826fab858" />

1.5: Настройка NTP-клиента на MLS

<img width="565" height="262" alt="image" src="https://github.com/user-attachments/assets/036b716a-7b73-462b-8877-a97368537d00" />

1.6: Проверка NTP
На R1, R2, R3, MLS:

<img width="1127" height="225" alt="image" src="https://github.com/user-attachments/assets/e89da7ea-4e91-4c80-9a45-abc0e61d9e97" />

<img width="1181" height="229" alt="image" src="https://github.com/user-attachments/assets/4a002956-5c77-4cf0-aa42-b2e90971fe66" />

<img width="1128" height="229" alt="image" src="https://github.com/user-attachments/assets/fcd94f6c-1d97-431f-baaa-94ca4fe868d0" />

<img width="1130" height="230" alt="image" src="https://github.com/user-attachments/assets/91aa599f-dfbe-4ae4-a6e3-94716853dc41" />

1.7: Настройка Syslog на всех устройствах
На R1, R2, R3, MLS:

<img width="652" height="267" alt="image" src="https://github.com/user-attachments/assets/133d86fb-ce49-4ea7-8c2f-dd39e583a409" />

<img width="689" height="339" alt="image" src="https://github.com/user-attachments/assets/b9fed924-b0b2-477d-acd1-825b81923306" />

<img width="683" height="322" alt="image" src="https://github.com/user-attachments/assets/de72aacf-affc-47f9-851d-6151e427de40" />

<img width="661" height="363" alt="image" src="https://github.com/user-attachments/assets/adec2a65-5179-48fa-934a-647af93eded3" />

1.8: Настройка Server0 как Syslog-сервера

<img width="687" height="546" alt="image" src="https://github.com/user-attachments/assets/1d292e21-a939-4d23-b748-2771b6618f7f" />

1.9: Проверка Syslog

<img width="1919" height="535" alt="image" src="https://github.com/user-attachments/assets/a250924c-e87a-4a72-8700-7d044a472221" />

Шаг 2: Включение SNMP на R2 и R3
На R2:

<img width="639" height="307" alt="image" src="https://github.com/user-attachments/assets/049d86d5-c42e-4958-9623-48eaf23e3a3a" />

На R3:

<img width="616" height="294" alt="image" src="https://github.com/user-attachments/assets/be8cb005-9f02-4320-85e4-66363c209777" />

Шаг 3: Настройка AAA и Telnet на R3
3.1: Настройка Server0 как AAA-сервера

<img width="697" height="701" alt="image" src="https://github.com/user-attachments/assets/1757cbb8-e8b1-4b78-b360-dfc33c08df94" />

3.2: Настройка локального пользователя на R3

<img width="552" height="186" alt="image" src="https://github.com/user-attachments/assets/51abea6c-9ea1-4192-bece-0b2272f64596" />

3.3: Настройка AAA на R3

<img width="616" height="168" alt="image" src="https://github.com/user-attachments/assets/69cd035e-1492-4c10-a63c-84c053bbe196" />

3.4: Включение Telnet на R3

<img width="544" height="270" alt="image" src="https://github.com/user-attachments/assets/3a07b578-5cf9-40dc-a565-0f21b37accf7" />

3.5: Проверка Telnet с AAA

<img width="631" height="195" alt="image" src="https://github.com/user-attachments/assets/6628ea16-c7fc-4443-b3d2-d947538865ef" />

3.6: Проверка резервного локального пользователя
1. На **Server0** → **Services** → **AAA** → выключаем временно **Service** (**Off**).
2. Снова выполним Telnet с R2:

<img width="654" height="184" alt="image" src="https://github.com/user-attachments/assets/c4f33c45-fc88-48f5-838a-2d148e9f043c" />

Шаг 4. Настройка FTP на R2
4.1: Настройка Server0 как FTP-сервера

<img width="705" height="476" alt="image" src="https://github.com/user-attachments/assets/c177f284-6dd1-44df-8e03-4c523450b9a9" />

4.2: Настройка FTP-клиента на R2

<img width="672" height="340" alt="image" src="https://github.com/user-attachments/assets/689451ee-560a-48ab-bbfa-5e9a75efcfa0" />

Шаг 5. Отправка конфигурации R2 на FTP

<img width="450" height="150" alt="image" src="https://github.com/user-attachments/assets/d68cfd04-b43b-4ce9-9803-ddc58ad6fc48" />

Шаг 6. Отправка конфигурации R3 на TFTP
6.1: Настройка Server0 как TFTP-сервера

<img width="693" height="375" alt="image" src="https://github.com/user-attachments/assets/37fb748f-b311-47d1-9c21-a14c2606d9f8" />

6.2: Отправка конфигурации с R3

<img width="581" height="178" alt="image" src="https://github.com/user-attachments/assets/e350806b-3f12-4872-9093-f4c4d2a11f19" />

Проверка:

<img width="704" height="696" alt="image" src="https://github.com/user-attachments/assets/b5b64ca7-2563-4be4-8509-5414532ffd7b" />

Шаг 7. Проверка отсутствия boot system на R3

<img width="485" height="70" alt="image" src="https://github.com/user-attachments/assets/8afff8e5-2702-4e8d-811b-cb998dbeac9d" />

Шаг 8. Telnet с R2 на R3 по имени "standby"
8.1: Настройка локального имени на R2

<img width="593" height="220" alt="image" src="https://github.com/user-attachments/assets/ee380bff-ef58-4dbf-baef-89780c0060ed" />

8.2: Telnet по имени
На R2:

<img width="642" height="223" alt="image" src="https://github.com/user-attachments/assets/323d83be-bb21-42c0-92a9-566864faf0ca" />

Шаг 9. Изменение локального имени пользователя в R3 через восстановление пароля
9.1: Процедура восстановления пароля

<img width="607" height="355" alt="image" src="https://github.com/user-attachments/assets/47727f55-10e5-4202-99fd-a43f85527a7f" />

Устройство перезагрузится и загрузится без пароля. После загрузки войдём в привилегированный режим.
Скопируем сохранённую конфигурацию в текущую:

<img width="628" height="291" alt="image" src="https://github.com/user-attachments/assets/15440b44-2ad3-4f2b-8687-0dc9063123e4" />

Изменим имя локального пользователя:

<img width="528" height="165" alt="image" src="https://github.com/user-attachments/assets/db4a74fb-886c-420e-8943-74dc02c62ade" />

Вернём регистр конфигурации в нормальное состояние:

<img width="471" height="76" alt="image" src="https://github.com/user-attachments/assets/5bd355bf-5736-4bb9-887f-2676b80238de" />

После перезагрузки, войдём под новым пользователем:

<img width="645" height="276" alt="image" src="https://github.com/user-attachments/assets/fa3d3bfb-a77a-4617-bb67-17e233d6f250" />

<img width="1548" height="740" alt="image" src="https://github.com/user-attachments/assets/cba8414b-2a61-4519-bde0-ffec83d58ba2" />

После процедуры восстановления пароля конфигурация была восстановлена из startup-config, регистр конфигурации возвращён в 0x2102. Связность всех интерфейсов восстановлена.

<img width="576" height="140" alt="image" src="https://github.com/user-attachments/assets/da79fec5-44e4-4ea8-9252-9eb3935762dc" />

<img width="1663" height="745" alt="image" src="https://github.com/user-attachments/assets/68555a00-b3cb-4556-8015-e4ba7a1d3a34" />
