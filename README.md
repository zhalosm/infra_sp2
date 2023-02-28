# Api_yamdb

Rest api проекта yamdb. Проект собирает отзывы пользовтелей на произведения - книги, музыка, фильмы. 
Приозведения деляться на жанры, категории и имеют рейтинг.


# Запуск проекта в контейнере

Клонировать репозиторий:

```
git clone https://github.com/ViTalityGH/api_yamdb.git
```

Перейти в папку с файлом docker-compose.yaml:

```
cd infra
```

Собираем контйенеры и запускаем их:

```
docker-compose up -d --build
```

Выполняем миграцию:

```
docker-compose exec web python manage.py migrate
```

Создаем суперпользователя:

```
docker-compose exec web python manage.py createsuperuser
```

Собираем статику:

```
docker-compose exec web python manage.py collectstatic --no-input
```

Следующим шагом создайте дамп (резервную копию) базы:

```
docker-compose exec web python manage.py dumpdata > fixtures.json
```

Остновка и удаление контйенров.

```
docker-compose down -v
```

# Шалблон наполнения env-файла:

```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

# Документация доступна по эндпойнту: http://localhost/redoc/
