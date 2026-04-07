# Todo List REST API (Spring Boot)

![Status](https://img.shields.io/badge/status-in%20development-yellow)
![Version](https://img.shields.io/badge/version-1.0-blue)
![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5-green)

Простое и надёжное приложение для управления задачами с REST API и веб-интерфейсом.

## Возможности

- Создание задач (POST `/api/tasks`)
- Просмотр всех задач (GET `/api/tasks`)
- Просмотр задачи по ID (GET `/api/tasks/{id}`)
- Обновление задачи (PUT `/api/tasks/{id}`)
- Удаление задачи (DELETE `/api/tasks/{id}`)
- Отметка о выполнении (через checkbox на фронтенде)
- **Веб-интерфейс на HTML/CSS/JS**
- **Автоматическое создание таблиц в PostgreSQL**

## Как запустить

### Требования

- Java 17+
- PostgreSQL
- Maven (или встроенный Maven Wrapper)

### Установка и запуск

1. **Создайте базу данных PostgreSQL**
   ```sql
   CREATE DATABASE todo_db;

2. **Настройте подключение к базе данных**
- Скопируйте application-example.properties в application.properties
- Укажите свой пароль от PostgreSQL

3. **Запустите приложение**
    ```bash
   # Через Maven Wrapper
    ./mvnw spring-boot:run

    # Или через Maven
    mvn spring-boot:run
   
4. **Откройте в браузере**
    ```text
   http://localhost:8080

### Пример работы через терминал (curl)
    ```bash
    # Создать задачу
    curl -X POST http://localhost:8080/api/tasks \
    -H "Content-Type: application/json" \
    -d '{"title":"Учить Java","description":"Spring Boot","completed":false}'

    # Получить все задачи
    curl http://localhost:8080/api/tasks

    # Обновить задачу (отметить выполненной)
    curl -X PUT http://localhost:8080/api/tasks/1 \
    -H "Content-Type: application/json" \
    -d '{"title":"Учить Java","description":"Spring Boot","completed":true}'

    # Удалить задачу
    curl -X DELETE http://localhost:8080/api/tasks/1

## API Эндпоинты

| Метод | Эндпоинт | Описание |
|-------|----------|----------|
| GET | `/api/tasks` | Получить все задачи |
| GET | `/api/tasks/{id}` | Получить задачу по ID |
| POST | `/api/tasks` | Создать задачу |
| PUT | `/api/tasks/{id}` | Обновить задачу |
| DELETE | `/api/tasks/{id}` | Удалить задачу |

## Обработка ошибок

Программа корректно реагирует на ошибки:

| Ситуация | Реакция программы |
|----------|-------------------|
| Задача не найдена | HTTP 404 + сообщение "Task not found" |
| Некорректный JSON | HTTP 400 Bad Request |
| Сервер не запущен | Ошибка подключения на фронтенде |
| БД недоступна | Ошибка при запуске приложения |

## Структура проекта
    todo-api/
    ├── src/main/java/com/lanaraw/todo/
    │   ├── controller/     # REST эндпоинты
    │   ├── service/        # Бизнес-логика
    │   ├── repository/     # Работа с БД
    │   └── entity/         # Модели данных
    ├── src/main/resources/
    │   ├── static/         # Фронтенд (HTML/CSS/JS)
    │   ├── application.properties
    │   └── application-example.properties
    └── pom.xml             # Зависимости


## Технологии

### Бэкенд
- Java 17
- Spring Boot 3.2
- Spring Data JPA
- PostgreSQL
- Maven

### Фронтенд
- HTML5
- CSS3
- Vanilla JavaScript (Fetch API)

## Планы по улучшению

- [ ] Добавить аутентификацию пользователей
- [ ] Добавить сроки выполнения задач
- [ ] Добавить категории для задач
- [ ] Написать юнит-тесты
- [ ] Добавить Docker

## Автор

**Lana Raw**

- GitHub: [@LanaRaw](https://github.com/LanaRaw)

## Статус

🚧 **В разработке (версия 1.0)**

На данный момент реализован базовый функционал:
- CRUD операции работают
- Есть веб-интерфейс

Чего пока нет:
- Валидации ввода
- Нормальной обработки ошибок
- Юнит-тестов