
---

## Для DevOps3 (файл `variant-1/README.md`):

# WordPress + MySQL + Redis (Docker Compose)

## Описание стека

Проект разворачивает полноценную CMS WordPress с базой данных MySQL и кэшированием Redis в изолированных Docker-контейнерах.

### Сервисы

| Сервис | Образ | Порт | Назначение |
|--------|-------|------|------------|
| **WordPress** | `wordpress:6.5` | `8080:80` | CMS-платформа |
| **MySQL** | `mysql:8.0` | `3306` (внутренний) | База данных |
| **Redis** | `redis:7-alpine` | `6379` (внутренний) | Кэш объектов |

## Какой вариант задания выбран и почему

Выбран **Вариант 1 — «Блог-платформа: WordPress + MySQL + Redis»**.

Проект использует готовые образы из Docker Hub, не требует написания кастомных Dockerfile и полностью соответствует требованиям задания: три сервиса, именованные тома, healthcheck для MySQL и политика перезапуска для всех контейнеров.

## Инструкция по запуску


# 1. Клонирование репозитория
```bash
git clone git@github.com:Saromych/DevOps3.git
cd DevOps3/variant-1
```

# 2. Настройка переменных окружения
```bash
cp .env.example .env
```
# При необходимости отредактируйте .env (пароли уже заданы для примера)

# 3. Запуск проекта
```bash
docker-compose up -d
```

# 4. Проверка статуса
```bash
docker-compose ps
```

# Ожидаемый вывод:
#   Name                Command                  State                      Ports
# -----------------------------------------------------------------------------------------------
# wp-app     docker-entrypoint.sh apach ...   Up             0.0.0.0:8080->80/tcp
# wp-mysql   docker-entrypoint.sh mysqld      Up (healthy)   3306/tcp, 33060/tcp
# wp-redis   docker-entrypoint.sh redis ...   Up (healthy)   6379/tcp

# 5. Доступ к WordPress
# Откройте в браузере: http://localhost:8080
# Пройдите стандартную установку WordPress (выберите язык, создайте учётную запись)


