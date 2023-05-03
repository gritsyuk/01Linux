## Part 1. Установка ОС
- ![part 1. OS Ubuntu](img/1.ubuntu.png)
>Отображает версию ОС

## Part 2. Создание пользователя
- ![part 2. User add](img/2.useradd.png)
>Создание нового пользователя и добавление его в группу 'adm'

## Part 3. Настройка сети ОС
- ![part 3. name PC](img/3.host_zone.png)
>Задача имя машины вида user-1 и установка временной зоны в соответсвии с текущим местоположением

- ![part 3. interfaces](img/4.iplink.png)
>Вывод названий сетевых интерфейсов
- lo (loopback device) – виртуальный интерфейс, присутствующий по умолчанию в любом Linux. Он используется для отладки сетевых программ и запуска серверных приложений на локальной машине. С этим интерфейсом всегда связан адрес 127.0.0.1. У него есть dns-имя – localhost. Посмотреть привязку можно в файле /etc/hosts..

- ![part 3. ip_DHCP](img/5.ip_a.png)
>ip адрес устройства от DHCP сервера
- Dynamic Host Configuration Protocol (DHCP) — сетевой протокол, предназначенный для автоматической конфигурации параметров сети на сетевых узлах.

- ![part 3. ip_a](img/5.ip_a.png)
>Внутренний ip адрес шлюза

- ![part 3. extr_ip](img/6.extr_ip.png)
>Внешний ip адрес

- ![part 3. netplan_apply](img/7.netplan_apply.png)
>вручную задаем статичные адреса

- Перезагрузить виртуальную машину. Убедиться, что статичные сетевые настройки (ip, gw, dns) соответствуют заданным в предыдущем пункте.

- ![part 3. ping](img/8.ping.png)
>пропинговать удаленные хосты 1.1.1.1 и google.com
## Part 4. Обновление ОС
- ![apt_upgrade](img/9.apt_upgrade.png)
>Обновление системных пакетов до последней версии через apt upgrade

## Part 5. Использование команды sudo
- sudo — это утилита, предоставляющая привилегии root для выполнения административных операций в соответствии со своими настройками. Она позволяет легко контролировать доступ к важным приложениям в системе. 
- ![sudo_rights](img/10.sudo_rights.png)
>предоставляем права root пользователю
- ![check_rights](img/11.check_rights.png)
>Переключаемся и проверяем права

- ![change_hostname](img/12.change_hostname.png)
>меняем имя хоста и проверяем

## Part 6. Установка и настройка службы времени
- ![timedate](img/13.timedate.png)
>синхронизиция времени через файл timesyncd.conf..

## Part 7. Установка и использование текстовых редакторов
- Использованы редакторы Vim, Nano, Joe
_установка: uudo apt install vim_
_sudo apt install nano_
_sudo apt install joe_

_создаем файлы *text_X.txt*_
- ![vim](img/14.vim_testX.png)
>Создание файла в vim : vim text_VIM.txt 2) Выйти c сохранениeм(esc) :wq!
- ![nano](img/15.nano_testX.png)
>Создание файла в nano : nano text_NANO.txt 2) Выйти c сохранениeм ^+O, ^+X
- ![joe](img/16.joe_testx.png)
>Создание файла в joe : joe text_JOE.txt 2) Выйти c сохранениeм ^K+X

_Редактируем файлы но не сохраняем, убеждаемся что пересохранения не было:_
- ![vim_edit](img/14.vim_testX.png)
>Выйти без сохранения(esc) :q!
- ![nano_edit](img/15.nano_testX.png)
>Выйти без сохранения ^+O
- ![joe_edit](img/16.joe_testx.png)
>Выйти без сохранения ^K+Z

- Функции поиска по содержимому файла (слово/cлова), замена:

- ![search_vim](img/20.search_vim.png)
- ![search_vim](img/20.search_vim_2.png)
>найти что-то в файле и заменить в редакторе VIM: %s/find_world/new_rold/g
- ![search_nano](img/21.search_nano.png)
- ![search_nano](img/21.search_nano_2.png)
>найти что-то в файле Cntr+W и заменить Cntr+W & Cntr+R
- ![search_joe](img/22.search_joe.png)
- ![search_joe](img/22.search_joe_2.png)
>найти что-то в файле ^K+F и заменить ^K+F: (R)eplace

## Part 8. Установка и базовая настройка сервиса SSHD

_Установить службу SSHd: sudo apt install openssh-server_
_Проверяем стату службы: systemctl status sshd_

- ![autostart_ssh](img/23.autostart_ssh.png)
>автостарт службы SSHd

- ![SSHd_port2022](img/24.SSHd_port2022.png)
>Перенастроить службу SSHd на порт 2022
>Рестарт сервиса: sudo systemctl restart ssh

- ![ps_ssh](img/25.ps_ssh.png)

- ps - выводит список текущих процессов на сервере. Флаги: -A, -e, (a) - выбрать все процессы; -a - выбрать все процессы, кроме фоновых; -d, (g) - выбрать все процессы, даже фоновые, кроме процессов сессий; -N - выбрать все процессы кроме указанных; -С - выбирать процессы по имени команды; -G - выбрать процессы по ID группы; -p, (p) - выбрать процессы PID; --ppid - выбрать процессы по PID родительского процесса; -s - выбрать процессы по ID сессии; -t, (t) - выбрать процессы по tty; -u, (U) - выбрать процессы пользователя.

- Перезагрузить систему: sudo reboot

_Установим netstat: sudo apt install net-tools_
- ![netstat_tan](img/26.netstat_tan.png)
>Вывод команды netstat -tan

- -a - Отображение всех подключений и ожидающих портов. -n - Отображение адресов и номеров портов в числовом формате. -t - Отображение текущего подключения в состоянии переноса нагрузки с процессора на сетевой адаптер при передаче данных ( "offload" ). 0.0.0.0 означает, что подключение может быть выполнено с/на любой адрес LISTEN - готовность к установке соединения

## Part 9. Установка и использование утилит top, htop

- ![top_screen](img/27_top_screen.png)
>Вывод комынды top
  * uptime = 24 min
  * количество авторизованных пользователей 1
  * общая загрузка системы - load avarage
  * общее количество процессов - tasks
  * загрузка cpu - %Cpu(s)
  * загрузка памяти - MiB mem

- ![top_mem](img/28_top_mem.png)
>pid процесса занимающего больше всего памяти Shift+m

- ![top_cpu](img/29_top_cpu.png)
>pid процесса, занимающего больше всего процессорного времени Shift+p

- ![htop_sort](img/30_htop_sort.png)
>Вывод htop с ссортировкой по PID, PERCENT_CPU, PERCENT_MEM, TIME

- ![htop_sshd](img/31_htop_sshd.png)
>отфильтрованному для процесса sshd

- ![htop_syslog](img/32_htop_syslog.png)
>с процессом syslog, найденным, используя поиск

- ![htop_setup](img/33_htop_setup.png)
>с добавленным выводом hostname, clock и uptime

## Part 10. Использование утилиты fdisk

- ![fdisk_l](img/34.fdisk_l.png)

## Part 11. Использование утилиты df

- ![df_root](img/35.df_root.png)
>Вывод команды df /
  * размер раздела - 7,865,580
  * размер занятого пространства - 3,063,896
  * размер свободного пространства - 4,380,616
  * процент использования - 42%
  * единицa измерения в выводе - Kb

- ![df_th](img/36.df_th.png)
>Вывод команды df -Th /
  * размер раздела - 7.6Gb
  * размер занятого пространства - 3.0Gb
  * размер свободного пространства - 4.2Gb
  * процент использования - 42%
  * единицa измерения в выводе - Gb

## Part 12. Использование утилиты du

- ![du_h](img/37.du_h.png)
>размер папок /home, /var, /var/log (в байтах, в человекочитаемом виде)

- ![du_varlog](img/38.du_varlog.png)
>размер всего содержимого в /var/log (не общее, а каждого вложенного элемента)

## Part 13. Установка и использование утилиты ncdu
_Установка: sudo apt install ncdu_

- ![ncdu_home_var](img/39.ncdu_home_var.png)
>размер /home /var

- ![ncdu_varlog](img/40.ncdu_varlog.png)
>размер /var/log

## Part 14. Работа с системными журналами

- ![session_root](img/42.session_root.png)
>время последней успешной авторизации, имя пользователя и метод входа в систему.

- ![ssh_restart](img/43.ssh_restart.png)
>перезапуск sshd service ssh restart


## Part 15. Использование планировщика заданий CRON

>с помощью команды crontab -e задаем задачу, что бы каждые 2 минуты выполнялся скрипт: */2 * * * * uptime

- ![crontab](img/44.crontab.png)
>смотрим в логах записи /var/log/syslog

- ![crontab remove](img/45.crontab_r.png)
>список текущих заданий, а затем их удаление