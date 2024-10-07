# FastAPI Project 

## Описание проекта

Это FastAPI проект разработан для практики, включает реализацию авторизации и использует PostgreSQL в качестве БД.

## Стек технологий

- **FastAPI** — высокопроизводительный веб-фреймворк для создания API
- **PostgreSQL** — реляционная БД
- **Docker** — инструмент для контейнеризации
- **Poetry** — управление зависимостями Python
- **Alembic** — управление миграциями БД

## Установка и запуск проекта

### 1. Клонирование репозитория

Склонируйте репозиторий проекта на ваш компьютер:
```bash
git clone https://github.com/deemmeeee/FastAPI-authorization-practice.git
```
### 2. Настройка переменных окружения
- Создайте файл `.env` в корневой директории проекта
- Скопируйте данные из файла `.env.example` в файл `.env`
- Добавьте свои данные в переменные для БД

### 3. Сборка и запуск Docker контейнеров
Для запуска контейнеров с приложением и БД выполните команду:
```bash
docker compose up --build
```
Это создаст и запустит контейнеры, установит зависимости с помощью Poetry и запустит приложение на порту 8000.

### 4. Применение миграций БД
После запуска контейнеров необходимо применить миграции к БД. Для этого выполните команду:
```bash
docker compose exec web alembic upgrade head
```

### 5. Остановка контейнеров
Чтобы остановить и удалить контейнеры, выполните следующую команду:
```bash
docker compose down
```
Если вы хотите удалить также все данные (включая содержимое БД), используйте:
```bash
docker compose down --volumes
```

## Структура проекта
```
├── alembic/                  # Директория для Alembic (миграции БД)
│   ├── env.py                # Файл настройки окружения Alembic
│   ├── versions/             # Содержит файлы миграций
│   └── script.py.mako        # Шаблон для новых миграций
├── app/                      # Основная директория FastAPI приложения
│   ├── core/                 # Основные настройки приложения
│   │   ├── config.py         # Конфигурационные переменные
│   │   └── database.py       # Настройки подключения к БД
│   ├── models/               # Модели данных
│   │   ├── mongodb/          # Модели для MongoDB
│   │   └── postgres/         # Модели для PostgreSQL
│   ├── repositories/         # Логика работы с данными
│   ├── routes/               # Определение маршрутов API
│   ├── schemas/              # Схемы данных для запросов/ответов(Pydantic)
│   ├── services/             # Сервисы, реализующие бизнес-логику
│   └── utils/                # Вспомогательные утилиты
├── media/                    # Директория для хранения загружаемых файлов
├── postgres_data/            # Данные БД
├── tests/                    # Тесты проекта
├── Dockerfile                # Dockerfile для сборки образа приложения
├── docker-compose.yml        # Конфигурация Docker Compose
├── poetry.lock               # Lock-файл с зависимостями проекта
├── pyproject.toml            # Файл с конфигурацией проекта и зависимостями
├── setup.cfg                 # Конфигурационный файл для линтеров и других инструментов
└── README.md                 # Документация проекта
```
## Ссылки

[О приложении](http://127.0.0.1:8000/admin)

[Swagger documentation](http://127.0.0.1:8000/docs/)
