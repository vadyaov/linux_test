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
* * addresses — ip адрес который будет назначен сетевой карте
* * gateway4 — ip адрес роутера
* * nameservers — DNS сервера. Первый - наш роутер
* * search - домен в котором будет произведен поиск. Домен можно настроить при помощи DNS сервера  

![after_config-file](/Screenshots/part_3.8.jpg)  
*end config file*  