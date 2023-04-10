## Проект YaMDb

Проект **YaMDb** собирает **отзывы (Review)** пользователей на **произведения (Titles)**. Произведения делятся на категории: "Книги", "Фильмы", "Музыка". Список **категорий (Category)** может быть расширен администратором.

Сами произведения в **YaMDb** не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

В каждой категории есть **произведения**: книги, фильмы или музыка. Например, в категории "Книги" могут быть произведения "Винни Пух и все-все-все" и "Марсианские хроники", а в категории "Музыка" — песня "Давеча" группы "Насекомые" и вторая сюита Баха.

Произведению может быть присвоен **жанр** (**Genre**) из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.

Благодарные или возмущённые пользователи оставляют к произведениям текстовые **отзывы** (**Review**) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — **рейтинг** (целое число). На одно произведение пользователь может оставить только один отзыв.


## Технологии

- Python 3.7

- Django 3.2

- Nginx

- Docker-compose


## Ресурсы API YaMDb

- Ресурс **auth**: аутентификация.

- Ресурс **users**: пользователи.

- Ресурс **titles**: произведения, к которым пишут отзывы (определённый фильм, книга или песенка).

- Ресурс **categories**: категории (типы) произведений («Фильмы», «Книги», «Музыка»).

- Ресурс **genres**: жанры произведений. Одно произведение может быть привязано к нескольким жанрам.

- Ресурс **reviews**: отзывы на произведения. Отзыв привязан к определённому произведению.

- Ресурс **comments**: комментарии к отзывам. Комментарий привязан к определённому отзыву.



## Шаблон наполнения env-файла:


1. Указываем, что работаем с postgresql:
```
DB_ENGINE=django.db.backends.postgresql
```
2. Указываем имя базы данных:
```
DB_NAME=postgres
```
3. Указываем логин для подключения к базе данных:
```
POSTGRES_USER=login
```
4. Указываем пароль для подключения к БД:
```
POSTGRES_PASSWORD=password
```
5. Указываем название сервиса (контейнера):
```
DB_HOST=db
```
6. Указываем порт для подключения к БД:
```
DB_PORT=5432
```

## Установка

Для запуска приложения проделайте следующие шаги:

1. Склонируйте репозиторий.
2. Перейдити в папку infra и запустите docker-compose.yaml (при установленном и запущенном Docker)
```
docker-compose up
```
3. Для пересборки контейнеров выполните команду:
```
docker-compose up -d --build
```
4. В контейнере web выполните миграции:
```
docker-compose exec web python manage.py migrate
```
5. Создатйте суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```
6. Соберите статику:
```
docker-compose exec web python manage.py collectstatic --no-input
```
Проект запущен и доступен по адресу: [localhost](http://localhost/admin/)


