# Домашнее задание к занятию «Уязвимости и атаки на информационные системы» Соловьев Д.В.

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.

------

### Задание 1

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя **nmap**.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

- Какие сетевые службы в ней разрешены?
- Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
  
*Приведите ответ в свободной форме.* 

Ответ:

1. Службы:
21/tcp   open  ftp; 
22/tcp   open  ssh;
23/tcp   open  telnet;
25/tcp   open  smtp;
53/tcp   open  domain;
80/tcp   open  http;
111/tcp  open  rpcbind;
139/tcp  open  netbios-ssn;
445/tcp  open  microsoft-ds;
512/tcp  open  exec;
513/tcp  open  login;
514/tcp  open  shell;
1099/tcp open  rmiregistry;
1524/tcp open  ingreslock;
2049/tcp open  nfs;
2121/tcp open  ccproxy-ftp;
3306/tcp open  mysql;
5432/tcp open  postgresql;
5900/tcp open  vnc;
6000/tcp open  X11;
6667/tcp open  irc;
8009/tcp open  ajp13;
8180/tcp open  unknown

2. Уязвимости:
А. https://www.exploit-db.com/exploits/6122
Б. https://www.exploit-db.com/exploits/16320
В. https://www.exploit-db.com/exploits/7855


### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

- Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
- Как отвечает сервер?

*Приведите ответ в свободной форме.*

Ответ:

При SYN сканировании не завершается "трёхкратное рукопожатие" , если хост отвечает пакетами с флагом SYN ACK, то порт открыт
FIN сканирование нужно для обхода файерволов. Отправляется пакет с флагом FIN , если хост отвечает RST то порт считается закрытым , 
соединения без ответа считается открытым . Xmas сканирование посылает пакеты с флагами FIN PSH URG и так же ответ RST говорит о закрытом порте, 
отстутствие ответа о открытом.
