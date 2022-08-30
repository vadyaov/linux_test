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