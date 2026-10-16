# API-документация (lab2, Node-RED)

Базовый URL: `http://localhost:1880`

## 1. GET /api/text

Возвращает простой текст.

**Запрос:** `GET http://localhost:1880/api/text`

**Ответ (200):**
```
Привет! Это простой текстовый ответ от Node-RED. Автор: Севашко Дарья.
```

## 2. GET /api/info

Возвращает JSON с двумя полями.

**Запрос:** `GET http://localhost:1880/api/info`

**Ответ (200):**
```json
{"app": "Node-RED Lab2", "author": "Севашко Дарья"}
```

## 3. GET /api/items/:id

Использует path-параметр `id` и query-параметры.

### Успешный запрос

**Запрос:** `GET http://localhost:1880/api/items/123`

**Ответ (200):**
```json
{"id": 123, "name": "Элемент #123", "query": {}, "message": "OK"}
```

### Запрос с query-параметрами

**Запрос:** `GET http://localhost:1880/api/items/5?filter=name&sort=asc`

**Ответ (200):**
```json
{"id": 5, "name": "Элемент #5", "query": {"filter": "name", "sort": "asc"}, "message": "OK"}
```

### Ошибка 400 — Bad Request

Если `id` не является числом.

**Запрос:** `GET http://localhost:1880/api/items/abc`

**Ответ (400):**
```json
{"error": "Bad Request", "message": "Параметр id должен быть числом", "received": "abc"}
```

### Ошибка 404 — Not Found

Если `id = 999`.

**Запрос:** `GET http://localhost:1880/api/items/999`

**Ответ (404):**
```json
{"error": "Not Found", "message": "Элемент с таким id не найден"}
```