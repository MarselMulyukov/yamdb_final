[![Django-app workflow](https://github.com/MarselMulyukov/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/MarselMulyukov/yamdb_final/actions/workflows/yamdb_workflow.yml)

# YamDB
Проект сервиса по сбору отзывов и оценок произведений различных категорий (книги, кино, музыка и т.п.) и жанров (драма, комедия, рок, джаз и т.п.).
Доступ к функционалу сервиса доступен только посредством API-запросов.

## Функционал сервиса
1. Регистрация новых пользователей. Авторизация существующих пользователей на основе токенов.
2. Разграничение пользователей в правах (администратор, модератор, аутентифицированный пользователь, аноним).
3. Добавление новых произведений, жанров и категорий.
4. Создание отзыва на произведение.
5. Создание комментария к отзыву.
6. Присвоение пользователем оценки произведению (по шкале от 1 до 10) и подсчет рейтинга произведения.

## Что сделано
1. Разработана API
2. Подготовлена инфраструктура для развертывания в трех docker контейнерах: web, db, nginx
3. Написан workflow GitHub actions на случай отправки нового коммита на GitHub, в нем следующие шаги:
- Автоматическое тестирование на PEP8 и пользовательские тесты
- Создание и отправка нового образа проекта на Docker Hub
- Деплой измененного проекта на удаленном сервере
- Отправка в телеграм сообщения об успешном деплое

## Проект также готов для запуска на локальной машине:
1. Склонировать репозиторий git clone https://github.com/MarselMulyukov/yamdb_final.git
2. Перейти в директорию с инфраструктурой cd yamdb_final/infra
3. Создать .env файл с переменными окружения по примеру env_example
4. Выполнить команду docker-compose -d --build
5. Выполнить команду docker-compose exec web python manage.py migrate
6. Выполнить команду docker-compose exec web python manage.py collectstatic
7. Выполнить команду docker-compose exec web python manage.py loaddata fixtures.json
8. Проект должен быть доступен по адресу localhost/
9. Админка должна быть доступна по адресу localhost/admin/

## Технологии
Django 3.0.5, Django RestFrameWork 3.11, PostreSQL, Docker Compose 3.8, GitHub Actions
 
## Авторы
Марсель при поддержке Яндекс.Практикум
