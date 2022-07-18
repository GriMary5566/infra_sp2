# api_yamdb
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). Произведения делятся на категории: «Книги», «Фильмы», «Музыка» и т.д. Список категорий (Category) может быть расширен администратором.

Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
Проект записан в образ. Образ размещен в реестре Docker Hub: mary5566/infra:v1.07.2022

## Requirements

- asgiref==3.2.10
- django==2.2.16
- django-filter==21.1
- djangorestframework==3.12.4
- djangorestframework-simplejwt==4.7.2
- drf-yasg==1.20.0
- gunicorn==20.0.4
- psycopg2-binary==2.8.6
- PyJWT==2.1.0
- pytest==6.2.4
- pytest-django==4.4.0
- pytest-pythonpath==0.7.3
- pytz==2020.1
- sqlparse==0.3.1
- requests==2.26.0

## Основные ресурсы api:

- AUTH - Регистрация пользователей и выдача токенов
- CATEGORIES - Категории (типы) произведений
- GENRES - Категории жанров
- TITLES - Произведения, к которым пишут отзывы (определённый фильм, книга или песенка).
- REVIEWS - Отзывы
- COMMENTS - Комментарии к отзывам
- USERS - Пользователи

Более подробнее см в /redoc/

## Как запустить проект:

Скачать образ из реестра Docker Hub :

```
docker pull mary5566/infra:v1.07.2022
```

Перейти в папку infra/ :

```
cd infra_sp2/infra/
```
Запустить docker-compose для сборки и запуска контейнеров:

```
docker-compose up -d --build
```

Выполнить миграции в контейнере web:

```
docker-compose exec web python manage.py migrate
```

Создать суперпользователя:

```
docker-compose exec web python manage.py createsuperuser
```
Собрать статику:

```
docker-compose exec web python manage.py collectstatic --no-input
```
Приложение успешно разворачивается локально и становится доступным по адресу http://localhost.
Проверить работоспособность приложения можно перейдя по адресу http://localhost/admin/.

## Примеры запросов:

К проекту подключен модуль redoc, содержащий документацию по доступным эндпоинтам и примерам запросов. Адрес для redoc - http://localhost/redoc/.

## Авторы проекта:

- Команда Яндекс.Практикума
- Дмитрий Филимонов - Тимлид
- Григорьева Мария - Разработчик
- Максимов Владислав - Разработчик
