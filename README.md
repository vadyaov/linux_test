## Part 1 Установка ОС ##

* cat /etc/issue - **определение дистрибутива linux(Debian)**

![linux ubuntu version](/Screenshots/part_1.jpg)
*linux ubuntu version*
            
## Part 2 Создание пользователя ##

* sudo adduser vad - **создание нового пользователя vad.**  
Вводим и подтверждаем пароль, оставляем настройки пользователя дефолтными.

![user creation](/Screenshots/part_2.1.jpg)
*user creation*  

* cat /etc/passwd - **текстовая база данных с информацией обо всех учетных записях linux**

![accounts info](/Screenshots/part_2.2.jpg)
*accounts info*  

## Part 3 Настройка сети ОС ##

* sudo hostname user-1 - **задаем название машины вида user-1**  

!["user-1" hostname](/Screenshots/part_3.1.jpg)
*"user-1" hostname*

* sudo timedatectl set-timezone Europe/Moscow - **Устанавливаем временную зону Europe/Moscow**  

![Europe/Moscow timezone](/Screenshots/part_3.2.jpg)
*Europe/Moscow timezone*  

Все файлы устройств сетевых интерфейсов находятся в папке /sys/class/net.
* ls /sys/class/net - **Выводим названия сетевых интерфейсов**  

![net interface](/Screenshots/part_3.3.jpg)  
*net interface*
> lo (loopback device) – виртуальный интерфейс, присутствующий по умолчанию в любом Linux. Он используется для отладки сетевых программ и запуска серверных приложений на локальной машине. С этим интерфейсом всегда связан адрес 127.0.0.1. У него есть dns-имя – localhost.

* ip addr show - **Получаем информацию о сетях, в том числе ip-адрес устройства**  

![ip-adress](/Screenshots/part_3.4.jpg)  
*ip-adress*  
* DHCP (англ. Dynamic Host Configuration Protocol — протокол динамической настройки узла) — прикладной протокол, позволяющий сетевым устройствам автоматически получать IP-адрес и другие параметры, необходимые для работы в сети TCP/IP. Данный протокол работает по модели «клиент-сервер».  

* wget -O - -q icanhazip.com. Для того чтобы определить внешний ip-адрес, воспользовались сервисом, так как ip addr показывает только локальные ip-адреса.  

![ip-adresses](/Screenshots/part_3.5.jpg)  
*ip-adresses*

* ip route | grep default - **Еще один вариант для получения внутреннего ip-адреса (ip-адреса по умолчанию)  

![ip-adress_in](/Screenshots/part_3.6.jpg)  
*ip-adress_in*  

* sudo vim /etc/netplan/00-installer-config.yaml - редактируем файл конфигурации netplan который находится в директории /etc/netplan/  
Вручную задаем статичные настройки ip, gw, dns.  

![config-file](/Screenshots/part_3.7.jpg)  
*init config file*  

* Основные настройки:  
  * addresses — ip адрес который будет назначен сетевой карте
  * gateway4 — ip адрес роутера
  * nameservers — DNS сервера

![after_config-file](/Screenshots/part_3.8.jpg)  
*after reboot config file*  

* ping 1.1.1.1 - 0% packet loss  

![1.1.1.1](/Screenshots/part_3.9.jpg)  
*1.1.1.1*  

* ping ya.ru - 0% packet loss  

![yandex](/Screenshots/part_3.10.jpg)  
*yandex*  

## Part 4 Обновление ##

* sudo apt-get update - синхронизация индекса пакетов из репозиториев.
* sudo apt-get upgrade - установка пакетов.  

![update](/Screenshots/part_4.1.jpg)  
*update*  

## Part 5 Sudo ##

* Команда **sudo** предоставляет возможность пользователям выполнять команды от имени суперпользователя root, либо других пользователей.
* sudo usermod -a -G sudo vad - предоставили пользователю vad права root
* sudo -u vad sudo hostname user-2 - изменили hostname на user-2 от пользователя vad  

![sudo](/Screenshots/part_5.1.jpg)  
*sudo*

## Part 6 Установка и настройка службы времени ##

* timedatectl и timedateclt show - информация о настройках времени

![timedatectl](/Screenshots/part_6.1.jpg)  
*timedatectl*

## Part 7 Vim Nano Emacs ##

### Vim ###

* vim test_vim.txt - создание файла
* i - переходим в режим insert
* ESC-->:wq - сохранить и выйти

![vim1](/Screenshots/part_7.1.jpg)  
*vim 1*

* vim test_vim.txt - открывает файл для редактирования
* dd - удалить строку на которой стоит курсор
* i - переходим в режим редактирования
* 21 School 21
* ESC-->:q - выход без сохранения изменений

![vim2](/Screenshots/part_7.2.jpg)  
*vim 2*

* /word - поиск слова

![vim3](/Screenshots/part_7.3.jpg)  
*vim 3*

* Чтобы заменить слово в строке на другое слово:
  * передвигаем курсор на строку с нужным словом
  * ESQ --> :s/old_word/new_word

![vim4](/Screenshots/part_7.4.jpg)  
*vim 4*

### Nano ###

*  nano test_nano.txt- создание файла
*  Ctrl + x - выйти
* nano спрашивает сохранить ли изменения - жмем *y* (Yes)

![nano1](/Screenshots/part_7.5.jpg)  
*nano 1*

* nano test_nano.txt - открывает файл для редактирования
* 21 School 21
* nano спрашивает сохранить ли изменения - жмем *n* (No)

![nano2](/Screenshots/part_7.6.jpg)  
*nano 2*

* Ctrl + W --> вводим слово --> Enter --> курсор стоит на нужном слове

![nano3](/Screenshots/part_7.7.jpg)  
*nano 3*

* Чтобы заменить слово в строке на другое слово:
  * Ctrl + \
  * вводим строку, которую необходимо перезаписать --> Enter

![nano5](/Screenshots/part_7.8.jpg)  
*nano 5*  
  * вводим строку, на которую необходимо произвести замену --> Enter

![nano6](/Screenshots/part_7.9.jpg)  
*nano 6* 
  * nano спрашивает, сделать ли данную замену - жмем *y* (Yes) 

![nano7](/Screenshots/part_7.10.jpg)  
*nano 7*

### Emacs ###

*  emacs test_emacs.txt - создание файла
* Сtrl + X --> Ctrl + C - выйти
* жмем *y* (Yes) для сохранения

![emacs1](/Screenshots/part_7.11.jpg)  
*emacs 1*

* emacs test_emacs.txt - открывает файл для редактирования
* 21 School 21
* Сtrl + X --> Ctrl + C - выйти
* жмем *n* (No) для выхода без сохранения

![emacs2](/Screenshots/part_7.12.jpg)  
*emacs 2*

* Ctrl + S - поиск строки вперед
* Ctrl + R - поиск строки назад
* сделаем Ctrl + S nano из второй строки --> курсор окажется на букве n слова nano следующей строки

![emacs3](/Screenshots/part_7.13.jpg)  
*emacs 3*

* Чтобы заменить слово в строке на другое слово:
  * команда query-replace - Alt + %
  * вводим строку, которую необходимо перезаписать --> Enter

![emacs4](/Screenshots/part_7.14.jpg)  
*emacs 4*

  * вводим строку, на которую необходимо произвести замену --> Enter

![emacs5](/Screenshots/part_7.15.jpg)  
*emacs 5*

  * ВАЖНО: курсор должен стоять выше (как минимум на одну строку) той строки, которую необходимо перезаписать

![emacs6](/Screenshots/part_7.16.jpg)  
*emacs 6*

## Part 8 Установка и базованя настройка сервиса SSHD ##

* sudo apt update - обновление индекса пакетов  
* sudo apt-get install ssh - установка ssh

![download](/Screenshots/part_8.1.jpg)
*download ssh*

* sudo apt install openssh-server - установка OpenSSH
* sudo systemctl enable sshd - добавляем пакет SSH-сервера в автозагрузку

![download](/Screenshots/part_8.2.jpg)
*ssh autorun*

* enabled на скриншоте - значит автозагрузка включена

* чтобы изменить порт (по умолчанию всегда 22): sudo vim /etc/ssh/sshd_config
* меняеv 22 на 2022

* Команда ps - информация о процессах. Ключи:
  * -A, -e - выбрать все процессы;
  * -a - выбрать все процессы, кроме фоновых;
  * -d - выбрать все процессы, даже фоновые, кроме процессов сессий;
  * -N - выбрать все процессы кроме указанных;
  * -С - выбирать процессы по имени команды;
  * -G - выбрать процессы по ID группы;
  * -p - выбрать процессы PID;
  * --ppid - выбрать процессы по PID родительского процесса;
  * -s - выбрать процессы по ID сессии;
  * -t - выбрать процессы по tty;
  * -u, (U) - выбрать процессы пользователя.

* Чтобы найти процесс sshd среди всех процессов, сначала узнаем PID sshd процесс с помощью команды systemctl status sshd, затем с помощью команды ps -p PID находим процесс sshd.

![sshd proc](/Screenshots/part_8.3.jpg)
*sshd process*

* netstat позволяет получить информацию об активности сетевых интерфейсов.
  * -a - Отображение всех подключений и ожидающих портов.
  * -b - Отображение исполняемого файла, участвующего в создании каждого подключения, или ожидающего порта.
  * -e - Отображение статистики Ethernet. Может применяться вместе с параметром -s.
  * -f - Отображение полного имени домена (FQDN) для внешних адресов.
  * -n - Отображение адресов и номеров портов в числовом формате.
  * -o - Отображение кода (ID) процесса каждого подключения.
  * -p протокол - Отображение подключений для протокола, задаваемых этим параметром.
  * -r - Отображение содержимого таблицы маршрутов.
  * -s - Отображение статистики протокола. Параметр -p позволяет указать подмножество выводимых данных.
  * -t - Отображение текущего подключения в состоянии переноса нагрузки с процессора на сетевой адаптер при передаче данных ( "offload" ).
  * -v - Подробный вывод информации, если это возможно.

![netstat](/Screenshots/part_8.4.jpg)
*netstat*

* 1 столбец - **Имя** - название протокола.
* 2 столбец - Счётчик байт не скопированных программой пользователя из этого сокета.
* 3 столбец - Счётчик байтов, не подтверждённых удалённым узлом.
* 4 столбец - **Локальный адрес** - локальный IP-адрес участвующий в соединении или связанный со службой, ожидающей входящие соединения (слушающей порт).  
  * Если в качестве адреса отображается 0.0.0.0 , то это означает - "любой адрес", т.е в соединении могут использоваться все IP-адреса существующие на данном компьютере.  
* 5 столбец - **Внешний адрес** - Внешний IP-адрес, участвующий в создании соединения.
* 6 стобец - **Состояние** - состояние соединения.
  * LISTEN (LISTENING)	- Ожидает входящих соединений.
  * SYN_SENT - Активно пытается установить соединение.

## Part 9 top htop ##

### top ###

![top](/Screenshots/part_9.1.jpg)  
*top*  
* uptime = 51 min
* 1 user
* load average — средняя загруженность системы одну минуту назад, пять и 15 соответственно
* Tasks - статистика процессов
  * total — общее количество процессов в системе
  * running — количество работающих в данный момент процессов
  * sleeping — количество ожидающих событий процессов
  * stopped — количество остановленных процессов
  * zombie — количество процессов, ожидающих родительский процесс для передачи статуса завершения
* % CPU - загрузка процессора
* Mem - информация об использовании физической оперативной памяти
* Swap - информация об использовании раздела подкачки
* PID 1243 - больше всего память (root процесс)

### htop ###

* сортировка по PID

![htop_PID](/Screenshots/part_9.2.jpg)  
*htop_PID*

* сортировка по PERCENT_CPU

![htop_CPU](/Screenshots/part_9.3.jpg)  
*htop_CPU*


* сортировка по PERCENT_MEM

![htop_MEM](/Screenshots/part_9.4.jpg)  
*htop_MEM*


* сортировка по TIME

![htop_TIME](/Screenshots/part_9.5.jpg)  
*htop_TIME*  

* sshd filter

![htop_sshd](/Screenshots/part_9.6.jpg)  
*htop_sshd*  

* search syslog

![htop_syslog](/Screenshots/part_9.7.jpg)  
*htop_syslog*

* +hostname, +uptime, +clock

![htop_add](/Screenshots/part_9.8.jpg)  
*htop_add*

## Part 10 fdisk ##

![fdisk](/Screenshots/part_10.jpg)  
*fdisk*  

## Part 11 df утилита ##

* df
* информация выводится в килобайтах 

![df](/Screenshots/part_11.1.jpg)  
*df*  

* df -Th
* вывод в более читаемом формате + тип файловой системы

![df](/Screenshots/part_11.2.jpg)  
*df -Th*  

## Part 12 du утлита ##

* home  
![du](/Screenshots/part_12.1.jpg)  
*du -h*  

* var  
![du](/Screenshots/part_12.2.jpg)  
*du -h*  

* var/log  
![du](/Screenshots/part_12.3.jpg)  
*du -h*

* var/log/*  
![du](/Screenshots/part_12.4.jpg)  
*du -h*

## Part 13 ncdu утлита ##

* home  
![ncdu](/Screenshots/part_13.1.jpg)  
*ncdu home* 

* var  
![du](/Screenshots/part_13.2.jpg)  
*ncdu var*  

* var/log  
![du](/Screenshots/part_13.3.jpg)  
*ncdu var/log*

## Part 14 Auth && SSH ##

![Auth](/Screenshots/part_14.1.jpg) 
*Auth*

![SSH](/Screenshots/part_14.2.jpg) 
*SSH*

