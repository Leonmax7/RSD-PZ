# HTTP-запити для ГЗ 1.1

Запусти сервер, потім виконай у CMD Windows:

```cmd
curl.exe -i http://localhost:8080/api/board-games
curl.exe -i http://localhost:8080/api/board-games/1
curl.exe -i http://localhost:8080/api/board-games/9999
```

Очікувано: список і одна картка = 200 OK; невідомий ID = 404 Not Found.
У цій роботі POST/PUT/DELETE поки що **не повинні бути реалізовані**.
