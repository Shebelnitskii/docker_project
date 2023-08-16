1. docker network create my-network
2. docker run -d --name django_app -p 8000:8000 -it python bash
3. docker run -d --name db_django -p 5432:5432 -e POSTGRES_PASSWORD=postgres -e POSTGRES_DB=lab -e POSTGRES_HOST_AUTH_METHOD=md5 postgres
4. docker network connect my-network django_app # Подключения сети my-network контейнера django_app
5. docker network connect my-network db_django # Подключения сети my-network контейнера db_django
6. Через терминал заходим  в постгрес: docker exec -it <айди контейнера> psql -U postgres 
7. Создать бд create database mydb
9. В пайчарме создать новый проект, установить через pip install Django, nano, psycopg2
10. django-admin startproject config . 
11. Настройки settings.py
    ALLOWED_HOSTS = ["127.0.0.1"]

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': 'mydb',
            'USER': 'postgres',
            'PASSWORD': 'postgres',
            'HOST': 'db_django', 
            'PORT': '5432',
                }
            } 
12. python manage.py makemigrations
13. Перезапуск докеров 
14. Запуск через ./manage.py runserver 0.0.0.0:8000