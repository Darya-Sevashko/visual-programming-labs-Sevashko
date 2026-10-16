# Отчёт по лабораторной работе №2 (Node-RED)

## Что сделано

В ходе работы я освоила Node-RED как low-code инструмент для визуального программирования. Установила Node-RED через Docker Desktop с volume, настроила порт 1880, создала 12 потоков (flow-01 … flow-12), охватывающих все обязательные ноды из задания. Каждый поток сохранён отдельным JSON-файлом в папке `lab2/flows/`, скриншоты — в `lab2/screenshots/`.

## Способ установки и версии

- **Способ**: Docker Desktop (образ `nodered/node-red:latest`).
- **Порт**: 1880.
- **Volume**: локальная папка `lab2/data` → `/data` в контейнере.

**Команда запуска:**

```
docker run -d --name node-red-lab2 -p 1880:1880 -v "//c/Users/USER/Desktop/visual-programming-labs-Sevashko/lab2/data:/data" nodered/node-red:latest
```

- **Node-RED version**: v5.0.8
- **Node.js version**: v24.21.0

## Использованные AI-промпты

Несколько ключевых примеров:

1. «Сгенерируй JavaScript-код для function node Node-RED, в котором используются let/const, if/else, цикл for, массив и объект. Функция должна возвращать объект с полем payload».
2. «Сгенерируй Mustache-шаблон для template node Node-RED, который формирует JSON из объекта с полями name, age, city».
3. «Как настроить http request node Node-RED для получения случайной шутки из публичного API api.chucknorris.io?».
4. «Как сделать счётчик в flow context Node-RED, который живёт между сообщениями?».
5. «Как настроить Node-RED в Docker с volume, чтобы данные сохранялись между перезапусками контейнера?».

## Освоенные ноды

- **Базовые**: inject, debug, function, switch, change, template.
- **Сетевые**: http request, http in, http response, mqtt in, mqtt out.
- **Dashboard**: gauge, chart (пакет node-red-dashboard).
- **Telegram**: telegram receiver, telegram sender (пакет node-red-contrib-telegrambot).
- **Работа с файлами**: write file, read file.
- **Контекст**: работа с flow.get() и flow.set() внутри function.

## Скриншоты всех flow

### 2.1 Inject → Debug
![Inject Debug](../screenshots/01-inject-debug.png)

### 2.2 Function
![Function](../screenshots/02-function.png)

### 2.3 Switch
![Switch](../screenshots/03-switch.png)

### 2.4 Change
![Change](../screenshots/04-change.png)

### 2.5 Template
![Template](../screenshots/05-template.png)

### 2.6 HTTP Request
![HTTP Request](../screenshots/06-http-request.png)

### 2.7 MQTT
![MQTT](../screenshots/07-mqtt.png)

### 2.8 GET-эндпоинты

**/api/text**
![Endpoints text](../screenshots/08-endpoints-text.png)

**/api/info**
![Endpoints info](../screenshots/08-endpoints-info.png)

**/api/items/123 — успех**
![Endpoints success](../screenshots/08-endpoints-success.png)

**/api/items/abc — 400**
![Endpoints 400](../screenshots/08-endpoints-error-400.png)

**/api/items/999 — 404**
![Endpoints 404](../screenshots/08-endpoints-error-404.png)

**/api/items/5?filter=name — query params**
![Endpoints query](../screenshots/08-endpoints-query.png)

### 2.9 Dashboard

**Страница /ui**
![Dashboard UI](../screenshots/09-dashboard-ui.png)

**Холст**
![Dashboard flow](../screenshots/09-dashboard-flow.png)

### 2.10 Telegram

**BotFather**
![Telegram botfather](../screenshots/10-telegram-botfather.png)

**Чат с ботом**
![Telegram chat](../screenshots/10-telegram-chat.png)

**Холст**
![Telegram flow](../screenshots/10-telegram-flow.png)

### 2.11 Файлы
![Files](../screenshots/11-files.png)

### 2.12 Контекст
![Context](../screenshots/12-context.png)
## Выводы

В ходе работы я научилась запускать Node-RED в Docker и работать с volume, чтобы данные сохранялись между перезапусками. Освоила базовые ноды (inject, debug, function, switch, change, template), научилась делать HTTP-запросы к публичным API, работать с MQTT-брокером, создавать REST-эндпоинты, дашборд с графиками, Telegram-бота, читать и записывать файлы, использовать flow context.

Самым интересным было увидеть, как из готовых блоков собирается полноценное приложение — почти без написания кода. Понравилось работать с Dashboard: gauge и chart сразу показывают результат. А также понравилось создавать GET-эндпоинты и смотреть на результаты работы прямо через браузер.

Node-RED — мощный инструмент для быстрого прототипирования. Он позволяет собрать рабочее приложение за минуты, а не часы.