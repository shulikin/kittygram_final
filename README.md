# Kittygram

Kittygram — социальная сеть для обмена фотографиями любимых питомцев с API

### Возможности проекта: 

Можно зарегистрироваться и авторизоваться, добавить нового котика на сайт или изменить существующего, добавить или изменить достижения, а также просмотреть записи других пользователей.

API для kittygram написан с использованием библиотеки **Django REST Framework**, используется **TokenAuthentication** для аутентификации, а также подключена библиотека **Djoser**.

### Технологии

- Python 3.9
- Django 3.2.3
- Django REST framework 3.12.4
- PostgreSQL
- Docker
- Nginx
- Gunicorn
- GitHub Actions

## Установка 

1. Клонируйте репозиторий на свой компьютер:

    ```bash
    git clone https://github.com/shulikin/kittygram_final.git
    ```
    ```bash
    cd kittygram
    ```
2. Создайте файл .env и заполните его своими данными. Перечень данных указан в корневой директории проекта в файле .env.example.


### Создание Docker-образов

1.  Замените username на ваш логин на DockerHub:

    ```bash
    cd frontend
    docker build -t username/kittygram_frontend .
    cd ../backend
    docker build -t username/kittygram_backend .
    cd ../nginx
    docker build -t username/kittygram_gateway . 
    ```

2. Загрузите образы на DockerHub:

    ```bash
    docker push username/kittygram_frontend
    docker push username/kittygram_backend
    docker push username/kittygram_gateway
    ```

### Настройка CI/CD

1. Файл workflow  находится в директории

    ```bash
    kittygram_final/.github/workflows/main.yml
    ```

2. Для адаптации его на своем сервере добавьте секреты в GitHub Actions:

    ```bash
    DOCKER_USERNAME                # имя пользователя в DockerHub
    DOCKER_PASSWORD                # пароль пользователя в DockerHub
    HOST                           # ip_address сервера
    USER                           # имя пользователя
    SSH_KEY                        # приватный ssh-ключ (cat ~/.ssh/id_rsa)
    SSH_PASSPHRASE                 # кодовая фраза (пароль) для ssh-ключа

    TELEGRAM_TO                    # id телеграм-аккаунта (можно узнать у @userinfobot, команда /start)
    TELEGRAM_TOKEN                 # токен бота (получить токен можно у @BotFather, /token, имя бота)
    ```