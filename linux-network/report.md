# DO2_Linux Network

## Part 1. Инструмент ipcalc

### 1.1. Сети и маски

* Адрес сети **192.167.38.54/13**: 192.160.0.0

* Перевод маски **255.255.255.0**
    * в префиксную запись: /24
    * в двоичную запись: 11111111.11111111.11111111.00000000

* Перевод маски **/15**
    * в обычную запись: 255.254.0.0
    * в двоичную запись: 11111111.11111110.00000000.00000000

* Перевод маски **11111111.11111111.11111111.11110000**
    * в обычную запись: 255.255.255.240
    * в префиксную запись: /28

* Минимальный и максимальный хост в сети **12.167.38.4** при масках
    * **/8**: 12.0.0.1 - 12.255.255.254
    * **11111111.11111111.00000000.00000000**: 12.167.0.1 - 12.167.255.254
    * **255.255.254.0**: 12.167.38.1 - 12.167.39.254
    * **/4**: 0.0.0.1 - 15.255.255.254

### 1.2. localhost

* Можно ли обратиться к приложению, работающему на localhost, со следующими IP:
    * **194.34.23.100**: нет
    * **127.0.0.2**: да
    * **127.1.0.1**: да
    * **128.0.0.1**: нет

### 1.3. Диапазоны и сегменты сетей

* Какие из перечисленных IP можно использовать в качестве публичного, а какие только в качестве частных:
    * **10.0.0.45**: частный
    * **134.43.0.2**: публичный
    * **192.168.4.2**: частный
    * **172.20.250.4**: частный
    * **172.0.2.1**: публичный
    * **192.172.0.1**: публичный
    * **172.68.0.2**: публичный
    * **172.16.255.255**: частный
    * **10.10.10.10**: частный
    * **192.169.168.1**: публичный

* Какие из перечисленных IP-адресов шлюза возможны у сети **10.10.0.0/18**:
    * **10.0.0.1**: нет
    * **10.10.0.2**: да
    * **10.10.10.10**: да
    * **10.10.100.1**: нет
    * **10.10.1.255**: да

## Part 2. Статическая маршрутизация между двумя машинами

* ![ip a](images/part2/1.png)  
*Вывод сетевых интерфейсов ws1*

* ![ip a](images/part2/2.png)  
*Вывод сетевых интерфейсов ws2*

* ![netplan](images/part2/3.png)  
*Описание сетевого интерфейса для ws1*

* ![netplan](images/part2/4.png)  
*Описание сетевого интерфейса для ws2*

* ![netplan](images/part2/5.png)  
*Применение сетевого интерфейса для ws1*

* ![netplan](images/part2/6.png)  
*Применение сетевого интерфейса для ws2*

### 2.1. Добавление статического маршрута вручную

* ![route](images/part2/7.png)  
*Добавление статического маршрута для ws1*

* ![route](images/part2/8.png)  
*Добавление статического маршрута для ws2*

* ![ping](images/part2/9.png)  
*Пинг соединения ws1-ws2*

* ![ping](images/part2/10.png)  
*Пинг соединения ws2-ws1*

### 2.2. Добавление статического маршрута с сохранением

* ![netplan](images/part2/11.png)  
*Добавление статического маршрута для ws1*

* ![netplan](images/part2/12.png)  
*Добавление статического маршрута для ws2*

* ![ping](images/part2/13.png)  
*Пинг соединения ws1-ws2*

* ![ping](images/part2/14.png)  
*Пинг соединения ws2-ws1*

## Part 3. Утилита iperf3

### 3.1. Скорость соединения

* 8 Mbps = 1 MB/s

* 100 MB/s = 819200 Kbps

* 1 Gbps = 1024 Mbps

### 3.2. Утилита iperf3

* ![iperf3](images/part3/1.png)  
*Запуск iperf3 на сервере ws1*

* ![iperf3](images/part3/2.png)  
*Результаты на клиенте ws2*

## Part 4. Сетевой экран

### 4.1. Утилита iptables

* ![firewall](images/part4/1.png)  
*Описание /etc/firewall.sh на ws1*

* ![firewall](images/part4/2.png)  
*Описание /etc/firewall.sh на ws2*

* ![firewall](images/part4/3.png)  
*Запуск фаервола на ws1*

* ![firewall](images/part4/4.png)  
*Запуск фаервола на ws2*

    * Оба файла содержат одни и те же правила, но в разном порядке. Именно порядок правил определяет итоговое поведение фаервола, потому что iptables обрабатывает правила сверху вниз до первого совпадения.

### 4.2. Утилита nmap

* ![ping](images/part4/5.png)  
*Пинг соединения ws1-ws2*

* ![ping](images/part4/6.png)  
*Пинг соединения ws2-ws1*

* ![nmap](images/part4/7.png)  
*Проверка состояния хоста ws1*

## Part 5. Статическая маршрутизация сети

Сеть:
![network](images/part5/network.png)

### 5.1. Настройка адресов машин

    eth0 = ens33
    eth1 = ens37

* ![netplan](images/part5/1.png)  
*Конфиг netplan для ws11*

* ![netplan](images/part5/2.png)  
*Конфиг netplan для ws21*

* ![netplan](images/part5/3.png)  
*Конфиг netplan для ws22*

* ![netplan](images/part5/4.png)  
*Конфиг netplan со статической маршрутизацией для r1*

* ![netplan](images/part5/5.png)  
*Конфиг netplan со статической маршрутизацией для r2*

* ![ip -4 a](images/part5/6.png)  
*Проверка адресов на ws11*

* ![ip -4 a](images/part5/7.png)  
*Проверка адресов на ws21*

* ![ip -4 a](images/part5/8.png)  
*Проверка адресов на ws22*

* ![ip -4 a](images/part5/9.png)  
*Проверка адресов на r1*

* ![ip -4 a](images/part5/10.png)  
*Проверка адресов на r2*

* ![ping](images/part5/11.png)  
*Пинг ws22 с ws21*

* ![ping](images/part5/12.png)  
*Пинг r1 с ws11*

### 5.2. Включение переадресации IP-адресов

* ![ip_forward](images/part5/13.png)  
*Включение переадресации ip для r1*

* ![ip_forward](images/part5/14.png)  
*Включение переадресации ip для r2*

* ![ip_forward](images/part5/15.png)  
*Включение постоянной переадресации ip для r1*

* ![ip_forward](images/part5/16.png)  
*Включение постоянной переадресации ip для r2*

### 5.3. Установка маршрута по умолчанию

* ![netplan](images/part5/17.png)  
*Добавление шлюза для ws11*

* ![netplan](images/part5/18.png)  
*Добавление шлюза для ws21*

* ![netplan](images/part5/19.png)  
*Добавление шлюза для ws22*

* ![ip r](images/part5/20.png)  
*Список маршрутов на ws11*

* ![ip r](images/part5/21.png)  
*Список маршрутов на ws21*

* ![ip r](images/part5/22.png)  
*Список маршрутов на ws22*

* ![ping](images/part5/23.png)  
*Пинг r2 с ws11*

* ![tcpdump](images/part5/24.png)  
*Входящие запросы на r2*

### 5.4. Добавление статических маршрутов

    Статические маршруты уже добавлены роутерам в п. 5.1

* ![ip r](images/part5/25.png)  
*Список маршрутов на r1*

* ![ip r](images/part5/26.png)  
*Список маршрутов на r2*

* ![ip r list](images/part5/27.png)  
*Маршруты до 10.10.0.0/18 и default на ws11*

    * Для адреса 10.10.0.0/18 был выбран маршрут, отличный от 0.0.0.0/0, по правилу самого длинного совпадения префикса.

### 5.5. Построение списка маршрутизаторов

* ![tcpdump](images/part5/28.png)  
*Запуск tcpdump на r1*

* ![traceroute](images/part5/29.png)  
*Список маршрутизаторов на пути от ws11 до ws21*

* ![tcpdump](images/part5/30.png)  
*Итоговый дамп на r1*

    * Принцип работы traceroute:  
    traceroute отправляет UDP-пакеты на целевой адрес, но с разным значением TTL. TTL - поле в IP-пакете. Каждый маршрутизатор уменьшает TTL на 1. Если TTL стал равен 0, маршрутизатор уничтожает пакет и отправляет обратно сообщение "ICMP time exceeded". Именно по этим ответам traceroute понимает, какие маршрутизаторы стоят на пути.

### 5.6. Использование протокола ICMP при маршрутизации

* ![tcpdump](images/part5/31.png)  
*Запуск tcpdump на r1*

* ![ping](images/part5/32.png)  
*Пинг несуществующего адреса с ws11*

* ![tcpdump](images/part5/33.png)  
*Итоговый дамп на r1*

## Part 6. Динамическая настройка IP с помощью DHCP

* ![netplan](images/part6/1.png)  
*Включение DHCP в netplan для ws21*

* ![dhcpd.conf](images/part6/2.png)  
*Настройка /etc/dhcp/dhcpd.conf на r2*

* ![resolv.conf](images/part6/3.png)  
*Настройка DNS в /etc/resolv.conf на r2*

* ![dhcp](images/part6/4.png)  
*Перезапуск службы DHCP на r2*

* ![reboot](images/part6/5.png)  
*Перезапуск ws21*

* ![ip a](images/part6/6.png)  
*Проверка выданного адреса на ws21*

* ![ping](images/part6/7.png)  
*Пинг ws22 с ws21*

* ![netplan](images/part6/8.png)  
*Установка MAC адреса и включение DHCP в netplan для ws11*

* ![dhcpd.conf](images/part6/9.png)  
*Настройка /etc/dhcp/dhcpd.conf на r1*

* ![resolv.conf](images/part6/10.png)  
*Настройка DNS в /etc/resolv.conf на r1*

* ![dhcp](images/part6/11.png)  
*Перезапуск службы DHCP на r1*

* ![reboot](images/part6/12.png)  
*Перезапуск ws11*

* ![ip a](images/part6/13.png)  
*Проверка выданного адреса на ws11*

* ![ping](images/part6/14.png)  
*Пинг ws21 с ws11*

* ![dhclient](images/part6/15.png)  
*Получение нового ip адреса на ws21*

    * Использовано:  
        * dhclient -r \<interface>
        * dhclient -v \<interface>

## Part 7. NAT

* ![apache2](images/part7/1.png)  
*Настройка общедоступности сервера apache2 в /etc/apache2/ports.conf на ws22*

* ![apache2](images/part7/2.png)  
*Настройка общедоступности сервера apache2 в /etc/apache2/ports.conf на r1*

* ![apache2](images/part7/3.png)  
*Запуск сервера apache2 на ws22*

* ![apache2](images/part7/4.png)  
*Запуск сервера apache2 на r1*

* ![firewall](images/part7/5.png)  
*Настройка фаервола на r2*

    * Политика по умолчанию: отбрасывать все маршрутизируемые пакеты

* ![firewall](images/part7/6.png)  
*Запуск фаервола на r2*

* ![ping](images/part7/7.png)  
*Пинг r1 с ws22*

* ![ping](images/part7/8.png)  
*Пинг ws22 с r1*

* ![firewall](images/part7/9.png)  
*Добавление правила в фаервол на r2*

    * Правило: разрешить маршрутизацию всех пакетов протокола ICMP

* ![firewall](images/part7/10.png)  
*Запуск фаервола на r2*

* ![ping](images/part7/11.png)  
*Пинг r1 с ws22*

* ![ping](images/part7/12.png)  
*Пинг ws22 с r1*

* ![firewall](images/part7/13.png)  
*Добавление правил в фаервол на r2*

    * Разрешить маршрутизацию пакетов уже установленных соединений

    * Маскирование всех локальных ip из сети 10.20.0.0/26 под r2 (SNAT)

    * Разрешить маршрутизацию tcp пакетов из сети 10.20.0.0/26 (для SNAT)

    * Перенаправлять tcp пакеты, предназначенные для r2:8080, на ws22:80 (DNAT)

    * Разрешить маршрутизацию tcp пакетов до ws22:80 (для DNAT)

* ![firewall](images/part7/14.png)  
*Запуск фаервола на r2*

* ![telnet](images/part7/15.png)  
*Проверка tcp соединения ws22 -> r1:80*

* ![telnet](images/part7/16.png)  
*Проверка tcp соединения r1 -> r2:8080 -> ws22:80*

## Part 8. Знакомство с SSH Tunnels

* ![firewall](images/part8/1.png)  
*Фаервол на r2*

* ![firewall](images/part8/2.png)  
*Запуск фаервола на r2*

* ![apache2](images/part8/3.png)  
*Настройка сервера apache2 на прослушивание localhost в /etc/apache2/ports.conf на ws22*

* ![apache2](images/part8/4.png)  
*Запуск сервера apache2*

* ![local tcp forwarding](images/part8/5.png)  
*Local TCP forwarding с ws21 до ws22*

* ![telnet](images/part8/6.png)  
*Проверка соединения ws21-ws22 (при открытой ssh сессии)*

* ![remote tcp forwarding](images/part8/7.png)  
*Remote TCP forwarding с ws11 до ws22*

* ![telnet](images/part8/8.png)  
*Проверка соединения ws11-ws22 (при открытой ssh сессии)*