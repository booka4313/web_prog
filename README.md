Реализация следующего функционала:

Авторизация и аутентификация пользователей
CRUD операции для сущностей
Наличие валидаций и обработка исключений
Наличие RESTful API
Использование unit и интеграционных тестов
Использование Django REST framework
Использование production-ready решений

Общая информация
Данный проект создан в следующем окружении:

Ubuntu 18.04.2 x86-64.
Python 3.6.7.
Django 2.2.1.
PostgreSQL 10.8
Запуск проекта
Установите Python development environment.

Установите PostgreSQL и создайте базу данных. Для создания базы данных выполните следующие шаги:

Запустите psql от имени пользователя postgres. Например, <psql -U postgres>.
Из коммандной строки psql выполните следующие комманды:
CREATE DATABASE catalogdb;
CREATE ROLE siteadmin WITH PASSWORD 'passwrd123';
ALTER ROLE siteadmin SET client_encoding TO 'utf8';
ALTER ROLE siteadmin SET default_transaction_isolation TO 'read committed';
ALTER ROLE siteadmin SET timezone TO 'Europe/Moscow';
GRANT ALL PRIVILEGES ON DATABASE catalogdb TO siteadmin;
ALTER ROLE siteadmin CREATEDB;
\q
Скопируйте файлы проекта в удобную для Вас папку. Перейдите в папку с файлом manage.py и выполните следующие комманды:
python3 manage.py makemigrations catalog
python3 manage.py migrate
python3 manage.py loaddata db.json
python3 manage.py runserver
Откройте в браузере страницу http://<IP_ADDRESS>:8000/admin/ для подключения к админке.

Логин: siteadmin
Пароль: passwrd123
Откройте в браузере страницу http://<IP_ADDRESS>:8000 для подключения к основному сайту. Различные пользователи (можно посмотреть в админке) имеют разные права на сайт. Пароли у всех одинаковые.

Вы можете протестировать сайт заранее подготовленными тестами из папки /catalog/tests. После выполнения теста не должно быть ни одной ошибки. Для теста перейдите в коневую папку проекта, где расположен файл manage.py и выполните команду:

python3 manage.py test
