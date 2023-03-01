# Api_yamdb

Rest api проекта yamdb. Проект собирает отзывы пользовтелей на произведения - книги, музыка, фильмы. 
Приозведения деляться на жанры, категории и имеют рейтинг.


# Стэк технологий

- Python
- Django Rest Framework
- Postgres
- Docker
- nginx

# Запуск проекта в контейнере

Клонировать репозиторий:

```
https://github.com/zhalosm/infra_sp2.git
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

Cоздание дамп (резервной копии) базы:

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

# Примеры запросов к API

Получение списка всех произведений

```
GET http://localhost/api/v1/titles/
```

Добавить новое произведение.
Права доступа: Администратор.

```
POST http://localhost/api/v1/titles/
```

Параметры json
```
{
"name": "string",
"year": 0,
"description": "string",
"genre": [
"string"
],
"category": "string"
}
```

Документация доступна по эндпойнту: http://localhost/redoc/

Авторы проекта:

Петров Константин, Виталий Коломойцев