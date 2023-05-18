# api_final

### Описание проекта
Данный проект реализует API для проекта YaTube. ЖЖ на минималках.
### Технологии
* Python 3.9
* Django 3.2
* Django Rest Framework 3.12
### Как запустить проект
Клонировать репозиторий и перейти в него в командной строке:
```
git clone git@github.com:fyurikon/api_final_yatube.git
```
```
cd api_final_yatube
```
Cоздать и активировать виртуальное окружение:
```
python3 -m venv env
```
* Если у вас Linux/macOS
    ```
    source env/bin/activate
    ```
* Если у вас windows
    ```
    source env/scripts/activate
    ```
```
python3 -m pip install --upgrade pip
```
Установить зависимости из файла requirements.txt:
```
pip install -r requirements.txt
```
Выполнить миграции:
```
python3 manage.py migrate
```
Запустить проект:
```
python3 manage.py runserver
```
### Примеры использования API
Cоздать суперпользователя:
```
python3 manage.py createsuperuser
```
Получаем токен через API:
```
http://127.0.0.1:8000/api/v1/jwt/create/
```
```json
{
    "username": "John Doe",
    "password": "ChangeMe!1"
}
```
Создать простой пост через API.
Выбираем HEADERS, в поле Key вводим Authorization в поле
Value вводим Bearer пробел и наш токен, полученный на предыдущем шаге.
```
Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXB...
```
```
http://127.0.0.1:8000/api/v1/posts/
```
```json
{
    "text": "Новый тестовый пост для проверки работоспособности API."
}
```

Выполняем POST-запрос, получаем ответ:
```json
{
    "id": 1,
    "text": "Новый тестовый пост для проверки работоспособности API.",
    "pub_date": "2023-05-18T17:25:43.741698Z",
    "author": "Leo",
    "image": null,
    "group": null
}
```
При создании поста можно ввести группу и добавить картинку.
JSON для создания поста, в общем виде, выглядит так:
```json
{
  "text": "string",
  "image": "string",
  "group": 0
}
```
Получить все посты используя GET-запрос:
```
http://127.0.0.1:8000/api/v1/posts/
```
С полной документацией к API можно всегдя ознакомиться по адресу:
```
http://127.0.0.1:8000/redoc/
```
