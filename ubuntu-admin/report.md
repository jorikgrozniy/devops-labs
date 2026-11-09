# DO1_Linux

## Part 1. Установка ОС

* ![cat /etc/issue](images/1.png)  
*Вывод версии Ubuntu*

## Part 2. Создание пользователя

* ![cat /etc/passwd](images/2.png)  
*Создание и вывод пользователя student с группой adm*

## Part 3. Настройка сети ОС

* ![set-hostname](images/3.png)  
*Установка имени хоста user-1*

* ![set-timezone](images/4.png)  
*Установка временной зоны*

* ![ip a](images/5.png)  
*Вывод сетевых интерфейсов*
    * lo - loopback-интерфейс. Это виртуальный сетевой интерфейс, который не связан ни с каким физическим оборудованием. Он нужен для того, чтобы компьютер мог обращаться к самому себе по сетевым протоколам.  

* ![sudo dhcpcd](images/6.png)  
*Получение ip устройства от DHCP*
    * DHCP (Dynamic Host Configuration Protocol) - протокол динамической настройки узла. Это сетевой протокол, позволяющий устройствам автоматически получать IP-адрес и другие параметры, необходимые для работы в сети.  

* ![curl ifconfig.me](images/7.png)  
*Вывод внешнего ip адреса*

* ![ip route | grep default](images/8.png)  
*Вывод внутреннего ip адреса*

* ![ls /etc/netplan](images/9.png)  
*Файл конфигурации netplan*

* ![netplan](images/10.png)  
*Измененный netplan со статичными ip, gw, dns*

* ![sudo netplan apply](images/11.png)  
*Применение netplan и перезагрузка*

* ![ip gw dns check](images/12.png)  
*Проверка статических ip, gw, dns*

* ![ping](images/13.png)  
*Проверка соединения пингом*

## Part 4. Обновление ОС

* ![sudo apt update](images/14.png)  
*Обновление списка пакетов*

* ![sudo apt upgrade](images/15.png)  
*Обновление системы*

* ![check](images/16.png)  
*Проверка отсутствия новых обновлений*

## Part 5. Использование команды sudo

* sudo (SuperUser DO) - это утилита в UNIX-подобных системах, позволяющая выполнять отдельные команды с привилегиями другого пользователя, не переключаясь полностью в его сессию.  

* ![sudo usermod](images/17.png)  
*Выдача пользователю student группы sudo*

* ![su student](images/18.png)  
*Установка пароля для пользователя student и переключение на него*

* ![set-hostname](images/19.png)  
*Установка имени хоста student-1 от имени student*

## Part 6. Установка и настройка службы времени

* ![systemd-timesyncd](images/20.png)  
*Проверка работы службы systemd-timesyncd и включение NTP*

* ![date](images/21.png)  
*Проверка времени*

* ![timedatectl show](images/22.png)  
*Проверка синхронизации времени*

## Part 7. Установка и использование текстовых редакторов

* ![sudo apt install vim nano mcedit](images/23.png)  
*Установка текстовых редакторов*

* ![vim](images/24.png)  
*Содержимое test_vim.txt*

    * Для выхода из vim с сохранением:  
    Esc -> ввести :wq -> Enter

* ![nano](images/25.png)  
*Содержимое test_nano.txt*

    * Для выхода из nano с сохранением:  
    Ctrl+O -> Enter -> Ctrl+X

* ![mcedit](images/26.png)  
*Содержимое test_mcedit.txt*

    * Для выхода из mcedit с сохранением:  
    F2 -> Enter -> F10

* ![vim](images/27.png)  
*Содержимое test_vim.txt после редактирования*

    * Для выхода из vim без сохранения:  
    Esc -> ввести :q! -> Enter

* ![nano](images/28.png)  
*Содержимое test_nano.txt после редактирования*

    * Для выхода из nano без сохранения:  
    Ctrl+X -> N

* ![mcedit](images/29.png)  
*Содержимое test_mcedit.txt после редактирования*

    * Для выхода из mcedit без сохранения:  
    F10 -> Выбрать No -> Enter

* ![vim](images/30.png)  
*Результат поиска в vim*

* ![vim](images/31.png)  
*Результат замены в vim*

    * Для замены слова в vim:  
    Esc -> ввести :s/слово/замена/ -> Enter

* ![nano](images/32.png)  
*Результат поиска в nano*

* ![nano](images/33.png)  
*Результат замены в nano*

    * Для замены слова в nano:  
    Ctrl+\ -> ввести слово -> Enter -> ввести замену -> Enter -> Y

* ![mcedit](images/34.png)  
*Результат поиска в mcedit*

* ![mcedit](images/35.png)  
*Результат замены в mcedit*

    * Для замены слова в mcedit:  
    F4 -> ввести слово -> ввести замену -> Enter -> выбрать Yes

## Part 8. Установка и базовая настройка сервиса SSHD

* ![sudo apt install openssh-server](images/36.png)  
*Установка службы ssh*

* ![sudo systemctl enable --now ssh](images/37.png)  
*Включение службы ssh и ее автозапуска*

* ![sudo vim /etc/ssh/sshd_config](images/38.png)  
*Открытие конфига sshd*

* ![port 2022](images/39.png)  
*Изменение порта*

* ![sudo systemctl restart ssh](images/40.png)  
*Перезапуск службы ssh*

* ![ps -fC sshd](images/41.png)  
*Вывод команды ps -fC sshd*

    * Команда ps (process status) используется для отображения информации о запущенных процессах в системе.
    * Ключи:
        * -C sshd (command) - выбрать процессы по точному имени исполняемого файла

        * -f (full format) - вывести расширенную информацию о процессе

* ![sudo reboot](images/42.png)  
*Перезапуск системы*

* ![ps -fC sshd](images/43.png)  
*Вывод команды netstat -tan*

    * Ключи:
        * -t (TCP) - показать только сокеты, работающие по протоколу TCP

        * -a (all) - показать все сокеты (в состоянии LISTEN)

        * -n (numeric) - отображать числовые значения IP-адресов и портов
    * Столбцы:
        * Proto - протокол, используемый сокетом

        * Recv-Q - количество байт, полученных от удалённого хоста и ожидающих обработки локальным приложением

        * Send-Q - количество байт, отправленных локальным приложением, но ещё не подтверждённых удалённой стороной

        * Local Address - локальный IP-адрес и порт, участвующие в соединении

        * Foreign Address - удалённый IP-адрес и порт
        
        * State - состояние TCP-сокета
    * 0.0.0.0 означает «все доступные IP-адреса на данной машине»

## Part 9. Установка и использование утилит top, htop

* ![sudo apt install htop](images/44.png)  
*Установка утилиты htop*

* ![top](images/45.png)  
*Вывод команды top*

    * uptime: 25 минут
    * Авторизованных пользователей: 1
    * Средняя загрузка системы:
        * 0.02 за 1 минуту
        * 0.02 за 5 минут
        * 0.03 за 15 минут
    * Общее количество процессов: 209
    * Загрузка cpu:
        * пользовательские: 0.2%
        * системные: 0.2%
        * свободно: 99.7%
    * Загрузка памяти:
        * всего: 3868 МБ
        * свободно: 2987 МБ
        * использовано: 452.4 МБ

* ![top](images/46.png)  
*Сортировка по памяти (Shift+M)*

    * pid процесса, занимающего больше всего памяти: 1629

* ![top](images/47.png)  
*Сортировка по процессорному времени (Shift+P)*

    * pid процесса, занимающего больше всего процессорного времени: 745

* ![htop](images/48.png)  
*Вывод htop, отсортированный по PID (F6)*

* ![htop](images/49.png)  
*Вывод htop, отсортированный по PERCENT_CPU (F6)*

* ![htop](images/50.png)  
*Вывод htop, отсортированный по PERCENT_MEM (F6)*

* ![htop](images/51.png)  
*Вывод htop, отсортированный по TIME (F6)*

* ![htop](images/52.png)  
*Вывод htop, отфильтрованный для процесса sshd (F4)*

* ![htop](images/53.png)  
*Вывод htop с процессом syslog, найденным, используя поиск (F3)*

* ![htop](images/54.png)  
*Вывод htop с добавленным выводом hostname, clock и uptime (F2 -> Meters)*

## Part 10. Использование утилиты fdisk

* ![sudo fdisk -l](images/55.png)  
*Вывод команды fdisk -l*

    * Имя жесткого диска: /dev/sda
    * Размер: 20 ГБ
    * Количество секторов: 41943040
    * Раздела подкачки нет

## Part 11. Использование утилиты df

* ![df](images/56.png)  
*Вывод команды df (корневой раздел /)*

    * Единица измерения: 1K-blocks (KiB)
    * Размер раздела: 10218772 КБ
    * Размер занятого пространства: 2996828 КБ
    * Размер свободного пространства: 6681272 КБ
    * Процент использования: 31%

* ![df -Th](images/57.png)  
*Вывод команды df -Th (корневой раздел /)*

    * Тип файловой системы: ext4
    * Размер раздела: 9.8 ГБ
    * Размер занятого пространства: 2.9 ГБ
    * Размер свободного пространства: 6.4 ГБ
    * Процент использования: 31%

## Part 12. Использование утилиты du

* ![du](images/58.png)  
*Вывод команды du*

* ![sudo du -s -b](images/59.png)  
*Размеры папок /home, /var, /var/log в байтах*

* ![sudo du -s -h](images/60.png)  
*Размеры папок /home, /var, /var/log в человекочитаемом виде*

* ![sudo du -s -h](images/61.png)  
*Размеры содержимого /var/log в человекочитаемом виде*

## Part 13. Установка и использование утилиты ncdu

* ![sudo apt install ncdu](images/62.png)  
*Установка утилиты ncdu*

* ![sudo ncdu /home](images/63.png)  
*Вывод размера /home через sudo ncdu /home*

* ![sudo ncdu /var](images/64.png)  
*Вывод размера /var через sudo ncdu /var*

* ![sudo ncdu /var/log](images/65.png)  
*Вывод размера /var/log через sudo ncdu /var/log*

## Part 14. Работа с системными журналами

* ![sudo tail /var/log/dmesg](images/66.png)  
*Вывод последних 10 записей из /var/log/dmesg*


* ![sudo tail /var/log/syslog](images/67.png)  
*Вывод последних 10 записей из /var/log/syslog*

* ![sudo tail /var/log/auth.log](images/68.png)  
*Вывод последних записей авторизации из /var/log/auth.log*

    * Время последней успешной авторизации: 2026-05-26 09:19:38+03:00
    * Пользователь: user
    * Метод входа: login

* ![sudo systemctl restart ssh](images/69.png)  
*Перезапуск службы ssh*

* ![sudo tail /var/log/syslog](images/70.png)  
*Вывод /var/log/syslog после перезапуска ssh*

## Part 15. Использование планировщика заданий CRON

* ![crontab -e](images/71.png)  
*Открытие планировщика заданий*

* ![crontab](images/72.png)  
*Добавление новой задачи*

* ![sudo tail /var/log/syslog](images/73.png)  
*Логи выполнения заданий CRON в /var/log/syslog*

* ![crontab -l](images/74.png)  
*Список заданий CRON*

* ![crontab -l](images/75.png)  
*Удаление всех заданий и вывод списка заданий CRON*