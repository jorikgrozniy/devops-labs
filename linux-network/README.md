# linux-network - DO2_Linux Network

Сети на стенде из 5 Linux-машин: маршрутизация, firewall/NAT, DHCP и SSH-туннели.

**Стенд:** ws11, ws21, ws22, r1, r2 - 3 хоста и 2 роутера. Топология: [network.png](images/part5/network.png)

**Что сделано:**
- расчёт подсетей, масок и диапазонов хостов через ipcalc;
- статические маршруты между двумя машинами и в схеме с двумя роутерами, IP forwarding;
- замер пропускной способности через iperf3, диагностика пути через traceroute и tcpdump;
- firewall на iptables: порядок правил, фильтрация, ICMP, проверка через nmap;
- DHCP-сервер: dhcpd.conf, привязка по MAC, dhclient, настройка DNS;
- NAT: SNAT для 10.20.0.0/26 и DNAT r2:8080 -> ws22:80, публикация Apache;
- SSH-туннели: local и remote TCP forwarding.

**Отчёт:** [report.md](report.md) - 8 разделов, 96 скриншотов.
