# HTTP-запити для ГЗ 1.2

Спочатку запусти сервер із папки `amazonua-gz12`.
**CMD Windows:** команди виконувати у корені цієї папки, де є каталог `examples/`.

```cmd
curl.exe -i http://localhost:8080/api/board-games
curl.exe -i http://localhost:8080/api/board-games/1
curl.exe -i http://localhost:8080/api/board-games/9999
curl.exe -i "http://localhost:8080/api/board-games?genre=Стратегія"

curl.exe -i -X POST http://localhost:8080/api/board-games -H "Content-Type: application/json; charset=utf-8" --data-binary "@examples/create-board-game.json"

curl.exe -i -X PUT http://localhost:8080/api/board-games/1 -H "Content-Type: application/json; charset=utf-8" --data-binary "@examples/update-board-game.json"

curl.exe -i -X DELETE http://localhost:8080/api/board-games/2
curl.exe -i -X DELETE http://localhost:8080/api/board-games/9999
```

Очікувано: GET = `200`, POST = `201`, PUT = `200`, DELETE = `204`,
неіснуючий ID для GET/PUT/DELETE = `404`. Після створення ID береться з відповіді сервера.

**Увага:** PUT/DELETE змінюють тестові дані до перезапуску. Після перезапуску знову
буде 5 початкових ігор. Якщо хочеш побачити JSON у браузері, досить GET-запитів.

Додатково для перевірки некоректних даних:
```cmd
curl.exe -i -X POST http://localhost:8080/api/board-games -H "Content-Type: application/json" -d "{}"
```
Очікувано `400 Bad Request` — поля з обов'язковими обмеженнями не заповнені.
