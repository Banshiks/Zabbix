Задание 1
Установите Zabbix Server с веб-интерфейсом.

Процесс выполнения
Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.
Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.
Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.
Требования к результаты
Прикрепите в файл README.md скриншот авторизации в админке.
Приложите в файл README.md текст использованных команд в GitHub.
Задание 2

Решение 1

![image](https://github.com/user-attachments/assets/deccf369-2be5-40b7-8167-bc999174dbf2)

Команды : 
1.sudo apt update
2.sudo dpkg -i zabbix-release_6.0-4+debian11_all.deb
3.sudo apt update
4.sudo apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
5.sudo -u postgres createuser --pwprompt zabbix
6.sudo -u postgres createdb -O zabbix zabbix
7.zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
8.nano /etc/zabbix/zabbix_server.conf параметр DBPassword=***
9.sudo systemctl restart zabbix-server zabbix-agent apache2
10.sudo systemctl enable zabbix-server zabbix-agent apache2


Задание 2
Установите Zabbix Agent на два хоста.

Процесс выполнения
Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
Установите Zabbix Agent на 2 вирт.машины, одной из них может быть ваш Zabbix Server.
Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов.
Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera.
Проверьте, что в разделе Latest Data начали появляться данные с добавленных агентов.
Требования к результаты
Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
Приложите в файл README.md текст использованных команд в GitHub

Решение 2


![image](https://github.com/user-attachments/assets/238b9f00-77cd-44f2-b064-6f704d3212f0)

![image](https://github.com/user-attachments/assets/3a6623c4-9dc5-4309-93f8-268168052763)

![iimage](https://github.com/user-attachments/assets/3d5a8710-43d1-4e42-b2b5-c72ccb49a4ea)

![image](https://github.com/user-attachments/assets/fd5577f9-9b0e-46a9-bb09-d32c75a78c85)

![image](https://github.com/user-attachments/assets/666f2284-0f05-49af-b912-0385f2692527)


1.sudo apt update
2.sudo dpkg -i zabbix-release_6.0-4+debian11_all.deb
3.sudo apt update
4.apt install zabbix-agent
5.systemctl restart zabbix-agent
6.systemctl enable zabbix-agent
7.sudo nano /etc/zabbix/zabbix_agentd.conf
8.systemctl restart zabbix-agent
