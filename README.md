# TODO Service

TODO Service — это REST API для управления списком задач. Реализован с использованием **FastAPI** и базы данных **SQLite**, с поддержкой контейнеризации через **Docker**.

---

## Функциональность
- **Создание задач** — добавление новой задачи в список.
- **Получение задач** — просмотр всех задач или конкретной по ID.
- **Обновление задач** — редактирование существующей задачи.
- **Удаление задач** — удаление задачи из списка.

---

## Установка и запуск

### Локально
1. **Клонируйте репозиторий:**
   ```bash
   git clone https://github.com/kokonafter/todo_service.git
   cd todo_service
2. **Установите зависимости:**
   ```bash
   pip install -r requirements.txt
3. **Запустите сервер:**
   ```bash
   uvicorn main:app --reload
4. **Откройте документацию API:**
Swagger UI: http://127.0.0.1:8000/docs
Redoc: http://127.0.0.1:8000/redoc

---

### Через Docker
1. **Соберите Docker-образ:**
   ```bash
   docker build -t todo-service .
2. **Запустите контейнер:**
   ```bash
   docker run -d -p 8000:80 -v todo_data:/app/data todo-service

---

## Эндпоинты
- **Основные маршруты**
  | Метод  | URL               | Описание                   |
  |--------|-------------------|----------------------------|
  | GET    | `/items`          | Получить список всех задач |
  | POST   | `/items`          | Создать новую задачу       |
  | GET    | `/items/{item_id}`| Получить задачу по ID      |
  | PUT    | `/items/{item_id}`| Обновить задачу по ID      |
  | DELETE | `/items/{item_id}`| Удалить задачу             |



- **Пример создания задачи**
POST /items
Тело запроса:
   ```json
   {
     "title": "Новая задача",
     "description": "Описание задачи",
     "completed": false
   }
Ответ:
   '''json
   
    {
    "title": "Новая задача",
    "description": "Описание задачи",
    "completed": false
    }

---

## Структура проекта
todo_app/
- database.py      — Конфигурация базы данных
- Dockerfile       — Конфигурация Docker
- main.py          — Основной файл приложения
- models.py        — Модели базы данных
- README.md        — Документация проекта
- requirements.txt — Зависимости проекта

data/
- todo.db          — Файл SQLite

__pycache__/
- database.cpython-39.pyc
- main.cpython-39.pyc
- models.cpython-39.pyc
   


