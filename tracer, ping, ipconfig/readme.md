### **Файл: 1.3.2.4 Lab - Tracing Internet Connectivity.pdf**

1. **Команда `tracert` (Windows) / `traceroute` (Linux, Unix, Cisco устройства)**:
   - **Определение**: Команда используется для определения маршрута, по которому пакеты данных проходят от исходного устройства до конечного.
   - **Как работает**:
     - Команда отправляет серию пакетов с увеличивающимся значением TTL (Time to Live).
     - Каждый маршрутизатор на пути уменьшает значение TTL на 1. Когда TTL достигает 0, маршрутизатор отправляет сообщение о превышении лимита времени (ICMP Time Exceeded) обратно отправителю.
     - Таким образом, команда `tracert` определяет IP-адреса всех маршрутизаторов на пути к конечному устройству.
   - **Пример команды**: `tracert www.cisco.com`.

2. **TTL (Time to Live)**:
   - **Определение**: TTL — это значение в заголовке IP-пакета, которое указывает, сколько "переходов" (hop) может пройти пакет, прежде чем будет отброшен.
   - **Назначение**: TTL предотвращает бесконечную циркуляцию пакетов в сети.
   - **Как работает**: Каждый маршрутизатор уменьшает TTL на 1. Если TTL достигает 0, пакет отбрасывается, и маршрутизатор отправляет сообщение ICMP Time Exceeded отправителю.

3. **ICMP (Internet Control Message Protocol)**:
   - **Определение**: Протокол ICMP используется для отправки сообщений об ошибках и диагностики в IP-сетях.
   - **Примеры сообщений**:
     - **Echo Request / Echo Reply**: Используются для команды `ping`.
     - **Time Exceeded**: Отправляется, когда TTL достигает 0.
     - **Destination Unreachable**: Отправляется, если пакет не может быть доставлен до конечного устройства.

---

### **Файл: 1.3.2.3 Lab - Building a Simple Network.pdf**

1. **Сеть (Network)**:
   - **Определение**: Сеть — это совокупность устройств (хостов, коммутаторов, маршрутизаторов), соединенных между собой для обмена данными.
   - **Основные компоненты сети**:
     - **Хосты (Hosts)**: Компьютеры, серверы, принтеры и другие устройства, которые могут отправлять и получать данные.
     - **Коммутаторы (Switches)**: Устройства, которые соединяют устройства в локальной сети (LAN) и передают данные между ними на основе MAC-адресов.
     - **Маршрутизаторы (Routers)**: Устройства, которые соединяют разные сети и передают данные между ними на основе IP-адресов.

2. **Кабели Ethernet**:
   - **Типы кабелей**:
     - **Прямой кабель (Straight-through cable)**:
       - **Определение**: Кабель, в котором провода на одном конце подключены к тем же контактам на другом конце.
       - **Использование**: Для подключения разных типов устройств, например, компьютера к коммутатору или маршрутизатору.
     - **Перекрестный кабель (Crossover cable)**:
       - **Определение**: Кабель, в котором провода на одном конце перекрещены относительно другого конца.
       - **Использование**: Для подключения однотипных устройств, например, компьютера к компьютеру или коммутатора к коммутатору.
   - **Разъемы**: Кабели Ethernet используют разъемы RJ-45.

3. **Настройка статического IP-адреса**:
   - **Определение**: Статический IP-адрес — это IP-адрес, который вручную назначается устройству и не изменяется.
   - **Как настроить**:
     - В Windows: Перейти в "Сетевые подключения" → "Свойства" → "Протокол Интернета версии 4 (TCP/IPv4)" → "Использовать следующий IP-адрес".
     - Указать IP-адрес, маску подсети и основной шлюз.
   - **Пример**: IP-адрес: 192.168.1.10, маска подсети: 255.255.255.0, основной шлюз: 192.168.1.1.

4. **Команда `ping`**:
   - **Определение**: Команда используется для проверки доступности устройства в сети.
   - **Как работает**: Команда отправляет ICMP Echo Request на указанный IP-адрес и ожидает ICMP Echo Reply.
   - **Пример команды**: `ping 192.168.1.11`.

---

### **Файл: 2.1.2.5 Lab - Determining the IP Address Configuration of a Computer.pdf**

1. **DHCP (Dynamic Host Configuration Protocol)**:
   - **Определение**: DHCP — это протокол, который автоматически назначает IP-адреса и другие параметры сети (маску подсети, основной шлюз, DNS-серверы) устройствам в сети.
   - **Этапы работы DHCP**:
     1. **DHCP Discover**: Клиент отправляет широковещательный запрос в сеть, чтобы найти DHCP-сервер.
     2. **DHCP Offer**: DHCP-сервер отвечает предложением IP-адреса и других параметров.
     3. **DHCP Request**: Клиент принимает предложение и запрашивает у сервера выделение этого IP-адреса.
     4. **DHCP Acknowledgment**: Сервер подтверждает выделение IP-адреса и отправляет клиенту окончательные параметры.
   - **Преимущества DHCP**:
     - Упрощает управление IP-адресами в больших сетях.
     - Автоматически обновляет параметры сети при изменении конфигурации.

2. **Команда `ipconfig /all`**:
   - **Определение**: Команда используется для отображения подробной информации о сетевых интерфейсах компьютера.
   - **Что отображает**:
     - IP-адрес, маску подсети, основной шлюз.
     - MAC-адрес (физический адрес).
     - DNS-серверы.
     - Состояние DHCP (включен/выключен).
     - Время аренды IP-адреса (lease time).

3. **Проверка подключения с помощью `ping`**:
   - **Проверка локального интерфейса**: `ping 127.0.0.1` (адрес обратной петли).
   - **Проверка подключения к другому устройству**: `ping <IP-адрес устройства>`.

---

### **Файл: 3.2.2.4 Lab - Determine the MAC Address of a Host.pdf**

1. **MAC-адрес (Media Access Control address)**:
   - **Определение**: MAC-адрес — это уникальный идентификатор, присвоенный сетевой интерфейсной плате (NIC) производителем.
   - **Формат**: 48 бит (6 байт), обычно записывается в виде шестнадцатеричных чисел, разделенных дефисами или двоеточиями (например, 00-1A-2B-3C-4D-5E).
   - **Структура**:
     - Первые 3 байта (OUI — Organizationally Unique Identifier) указывают производителя.
     - Последние 3 байта — уникальный идентификатор устройства.

2. **Команда `ipconfig /all`**:
   - **Определение**: Команда используется для отображения MAC-адреса и других параметров сетевого интерфейса.

---

### **Файл: 3.3.3.2 Lab - View Wireless and Wired NIC Information.pdf**

1. **Сетевые интерфейсные платы (NIC — Network Interface Card)**:
   - **Определение**: NIC — это аппаратное устройство, которое позволяет компьютеру подключаться к сети (проводной или беспроводной).
   - **Типы NIC**:
     - **Проводные (Ethernet NIC)**: Подключаются к сети через кабель Ethernet (RJ-45).
     - **Беспроводные (Wi-Fi NIC)**: Подключаются к сети через беспроводное соединение (Wi-Fi).
   - **MAC-адрес**: Каждая NIC имеет уникальный MAC-адрес, который используется для идентификации устройства в локальной сети.

2. **Беспроводные сети (Wi-Fi)**:
   - **Определение**: Беспроводные сети используют радиоволны для передачи данных между устройствами.
   - **SSID (Service Set Identifier)**:
     - **Определение**: SSID — это имя беспроводной сети, которое отображается при поиске доступных сетей.
     - **Пример**: "Home-Net", "Office-WiFi".
   - **Скорость беспроводного подключения**:
     - Зависит от стандарта Wi-Fi (например, 802.11n, 802.11ac, 802.11ax).
     - Современные стандарты поддерживают скорости до нескольких гигабит в секунду.

3. **Безопасность беспроводных сетей**:
   - **Методы шифрования**:
     - **WEP (Wired Equivalent Privacy)**: Устаревший метод, ненадежный.
     - **WPA (Wi-Fi Protected Access)**: Более безопасный, чем WEP, но также устаревший.
     - **WPA2/WPA3**: Современные стандарты шифрования, обеспечивающие высокий уровень безопасности.
   - **Ключ безопасности (Pre-shared Key)**: Пароль, который необходимо ввести для подключения к защищенной сети.

4. **Команда `ipconfig /all`**:
   - **Определение**: Команда используется для отображения информации о всех сетевых интерфейсах, включая MAC-адрес, IP-адрес, маску подсети, основной шлюз и DNS-серверы.
   - **Пример вывода**:
     ```
     Физический адрес (MAC): 00-1A-2B-3C-4D-5E
     IPv4-адрес: 192.168.1.10
     Маска подсети: 255.255.255.0
     Основной шлюз: 192.168.1.1
     ```

---

### **Файл: 3.4.3.5 Lab - Address Resolution Protocol (ARP).pdf**

1. **Протокол ARP (Address Resolution Protocol)**:
   - **Определение**: ARP используется для сопоставления IP-адреса (уровень 3) с MAC-адресом (уровень 2) в локальной сети.
   - **Как работает**:
     - Устройство отправляет широковещательный ARP-запрос с IP-адресом, для которого нужно найти MAC-адрес.
     - Устройство с соответствующим IP-адресом отправляет ARP-ответ, содержащий свой MAC-адрес.
   - **Пример**:
     - Компьютер A хочет отправить данные на компьютер B с IP-адресом 192.168.1.2.
     - Компьютер A отправляет ARP-запрос: "Кто имеет IP-адрес 192.168.1.2?"
     - Компьютер B отвечает: "Я имею IP-адрес 192.168.1.2, мой MAC-адрес — 00-1A-2B-3C-4D-5E."

2. **Кэш ARP**:
   - **Определение**: Кэш ARP — это таблица на устройстве, которая хранит сопоставления IP-адресов и MAC-адресов.
   - **Как просмотреть кэш ARP**:
     - В Windows: `arp -a`.
     - Пример вывода:
       ```
       Интерфейс: 192.168.1.10
         Интернет-адрес      Физический адрес      Тип
         192.168.1.1         00-1A-2B-3C-4D-5E     динамический
         192.168.1.2         00-1A-2B-3C-4D-5F     динамический
       ```
   - **Типы записей**:
     - **Динамические**: Записи, созданные автоматически в результате ARP-запросов.
     - **Статические**: Записи, добавленные вручную.

3. **Wireshark**:
   - **Определение**: Wireshark — это анализатор сетевых пакетов, который позволяет захватывать и анализировать сетевой трафик.
   - **Использование**:
     - Захват ARP-запросов и ответов.
     - Анализ заголовков пакетов (Ethernet, IP, ARP).

---

### **Файл: 3.5.2.5 Lab - Connect to a Wireless Router.pdf**

1. **Подключение к маршрутизатору**:
   - **Кабель Ethernet**:
     - Используется для подключения компьютера к маршрутизатору через порт LAN.
     - Тип кабеля: Прямой кабель (Straight-through cable).
   - **Настройка IP-адреса**:
     - **DHCP**: IP-адрес назначается автоматически.
     - **Статический IP**: IP-адрес настраивается вручную.

2. **Основной шлюз (Default Gateway)**:
   - **Определение**: Основной шлюз — это IP-адрес маршрутизатора, через который устройство выходит в интернет.
   - **Пример**: Если IP-адрес маршрутизатора — 192.168.1.1, то основной шлюз на компьютере должен быть настроен на 192.168.1.1.

3. **Команда `ping`**:
   - **Определение**: Команда используется для проверки подключения между устройствами.
   - **Пример**: `ping 192.168.1.1` (проверка подключения к маршрутизатору).

---

### **Файл: 4.1.1.2 Packet Tracer - Connecting to a Web Server.pdf**

1. **Подключение к веб-серверу**:
   - **Определение**: Веб-сервер — это устройство, которое предоставляет доступ к веб-страницам через протокол HTTP/HTTPS.
   - **Как подключиться**:
     - В браузере введите IP-адрес веб-сервера (например, 172.33.100.50).
   - **Пример**: Ввод `172.33.100.50` в адресной строке браузера откроет веб-страницу сервера.

2. **Команда `ping`**:
   - **Определение**: Команда используется для проверки доступности веб-сервера.
   - **Пример**: `ping 172.33.100.50`.

---

### **Файл: 4.1.4.4 Lab - Using Windows Calculator for Binary Conversions.pdf**

1. **Двоичная система счисления**:
   - **Определение**: Двоичная система использует только две цифры: 0 и 1.
   - **Пример**: Число 10 в двоичной системе — 1010.

2. **Преобразование IP-адресов**:
   - **Определение**: IP-адрес состоит из четырех октетов (8 бит каждый), которые можно преобразовать в двоичную форму.
   - **Пример**: IP-адрес 192.168.1.1 в двоичной форме:
     ```
     192 -> 11000000
     168 -> 10101000
     1   -> 00000001
     1   -> 00000001
     ```

3. **Маска подсети**:
   - **Определение**: Маска подсети определяет, какая часть IP-адреса относится к сети, а какая — к хосту.
   - **Пример**: Маска 255.255.255.0 в двоичной форме:
     ```
     255 -> 11111111
     255 -> 11111111
     255 -> 11111111
     0   -> 00000000
     ```

---
