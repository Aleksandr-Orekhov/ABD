1. Открываем терминал


![Image](https://user-images.githubusercontent.com/114604670/202368104-c308ecea-2d7f-4f4e-87ad-ebd822947398.png)

2. Выполняем обновление с помощью команд update и upgrate. 


![Image](https://user-images.githubusercontent.com/114604670/202368260-cf505dff-c15b-4d4e-87a4-46ecd9f9b061.png)

3. Распаковка пакетов при помощи кода: sudo apt-get install build-essential libreadline-dev zlib1g-dev flex bison libxml2-dev libxslt-dev libssl-dev
libxml2-utils xsltproc ccache


![Image](https://user-images.githubusercontent.com/114604670/202368394-996007e1-36f5-4fd8-9651-61d8c59b758e.png)

Выдало ошибку

![Image](https://user-images.githubusercontent.com/114604670/202368453-7ae57494-2407-410c-8e6d-43d60b101ab2.png)

Выполняем sudo mkdir -p /local/apps/postgresql/pgsql115/


![Image](https://user-images.githubusercontent.com/114604670/202368586-78120ca3-aa0d-4793-a0ac-3372f3a7ffd6.png)

4. Скачивание postgresql, распаковка и установка

curl -O https://ftp.postgresql.org/pub/source/v11.5/postgresql-11.5.tar.gz


![Image](https://user-images.githubusercontent.com/114604670/202368737-f339e37e-0053-4d44-a568-8e49f9ca42fc.png)

gunzip postgresql-11.5.tar.gz
tar -xvf postgresql-11.5.tar


![Image](https://user-images.githubusercontent.com/114604670/202368775-b7e8b0eb-e8ce-4d73-a127-cd1c4267487f.png)

Переходим в дирекорию и начинаем конфигурацию
cd postgresql-11.5
./configure --prefix=/local/apps/postgresql/pgsql115/ --with-pgport=5432


![Image](https://user-images.githubusercontent.com/114604670/202368838-813ae8a1-81a2-467d-a5e3-c9fab9eca3c3.png)

Данным способом не получилось, поэтому устанавливаем из пакетов.

1. Выполняем обновление
sudo apt update

2. Устанавливаем СУБД PostgreSQL:
sudo apt -y install postgresql


![Image](https://user-images.githubusercontent.com/114604670/202369017-80eed2d2-c698-4538-ad2c-e6d1adfac7dc.png)

НАСТРОЙКА POSTGRESQL В UBUNTU

1. После установки переключиться на пользователя postgres с помощью команды:

sudo -i -u postgres

2. После переключения на пользователя postgres, войти в консоль управления:

psql


![Image](https://user-images.githubusercontent.com/114604670/202369270-1d02e71d-09db-4e9c-928e-5db1ed3b8fc3.png)
3. Посмотреть информацию о соединении:

\conninfo


![Image](https://user-images.githubusercontent.com/114604670/202369359-470262c7-6838-4bf7-a58e-4c4c1d5d8cb5.png)

4. Чтобы выйти:

\q

5. Чтобы вернуться в свою директорию:

exit

УСТАНОВКА PGADMIN4 В UBUNTU

1. ПРОВЕРКА СИСТЕМНЫХ ТРЕБОВАНИЙ

Для того чтобы проверить состояние службы Postgresql выполните такую команду:

systemctl status postgresql

В поле status должно быть слово ative, выделенное зеленым цветом.


![Image](https://user-images.githubusercontent.com/114604670/202369544-244bf58f-6193-4ca4-82cd-06c4e7812759.png)

2. ДОБАВЛЕНИЕ РЕПОЗИТОРИЯ

Сначала установить публичный ключ при помощи команды:

sudo wget https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add packages_pgadmin_org.pub


![Image](https://user-images.githubusercontent.com/114604670/202369605-e647b2e8-01e9-444c-9c25-8cacb13fbdd0.png)

После этого добавить запись о репозотории pgAdmin в файл /etc/apt/sources.list.d/pgadmin4.list:

echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > sudo tee >>/etc/apt/sources.list.d/pgadmin4.list


![Image](https://user-images.githubusercontent.com/114604670/202369648-1aa858d7-94af-4d82-8916-2fa532732125.png)

Обновить:
sudo apt update

3. УСТАНОВКА PGADMIN4

Чтобы начать установку pgAdmin4:

sudo apt install pgadmin4


![Image](https://user-images.githubusercontent.com/114604670/202369745-6c3a66f1-3059-460f-937f-ec6077fe5099.png)

4. НАСТРОЙКА PGADMIN4
Чтобы запустить её откройте главное меню и введите в строке поиска pgAdmin, а затем кликните по иконке программы.


![Image](https://user-images.githubusercontent.com/114604670/202369848-783a57d8-0e30-42a8-9148-dfc618218757.png)



![Image](https://user-images.githubusercontent.com/114604670/202369869-73206ffc-d900-44de-aeed-c0bd493b05e7.png)



![Image](https://user-images.githubusercontent.com/114604670/202369878-c89ee39c-1ce3-4dd1-a26b-b500ffec20a6.png)

5. РУССИФИКАЦИЯ


![Image](https://user-images.githubusercontent.com/114604670/202370010-18e48c76-73b8-4b2c-baa9-8d3d9e470c4a.png)


![Image](https://user-images.githubusercontent.com/114604670/202370030-21ec7d4a-90f3-428b-a74e-043bf356a01c.png)

6. ДОСТУП К ВЕБ-ИНТЕРФЕЙСУ

Чтобы настроить web-интерфейс в терминале ввести следующую строку:

sudo /usr/pgadmin4/bin/setup-web.sh



![Image](https://user-images.githubusercontent.com/114604670/202370154-e10849f5-35e1-4b9f-96e2-eea7cbe1cfab.png)

Ввести адрес и пароль электронной почты и подождать

После окончания выполнения команды набрать в адресной строке браузера:

http://127.0.0.1/pgadmin4


![Image](https://user-images.githubusercontent.com/114604670/202370219-0fd61731-774b-4b2c-9e58-275a4fb75bd8.png)

УСТАНОВКА ЗАВЕРШЕНА

![Image](https://user-images.githubusercontent.com/114604670/202370243-251e9582-fa89-4bbd-a827-1ae8e611c7ad.png)