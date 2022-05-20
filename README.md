# Как запустить проект:

-   Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:ivMokretsov/api_final_yatube.git
cd api_final_yatube
```

-   Создать и активировать виртуальное окружение:

```
python -m venv env
source env/bin/activate
```

-   Установить зависимости из файла requirements.txt:
```
python -m pip install --upgrade pip
pip install -r requirements.txt
```

-   Выполнить миграции:

```
cd yatube_api
python manage.py migrate
```

-   Запустить проект:

```
python3 manage.py runserver
```
# Примеры API
### Получить список всех публикаций
**Запрос**

    GET http://127.0.0.1:8000/api/v1/posts?limit=2&offset=1
**Ответ**

    {
        "count": 3,
        "next": null,
        "previous": "http://127.0.0.1:8000/api/v1/posts/?limit=2",
        "results": [
            {
                "id": 2,
                "author": "string",
                "text": "string",
                "pub_date": "2022-05-20T12:25:50.462910Z",
                "image": null,
                "group": 1
            },
            {
                "id": 3,
                "author": "string",
                "text": "string",
                "pub_date": "2022-05-20T12:25:58.690456Z",
                "image": "string",
                "group": 0
            }
        ]
    }

### Подписка на автора
**Запрос**

    Post http://127.0.0.1:8000/api/v1/follow/
	    {
	    "following": "string"
	    }

**Ответ**

**200**:

    {
      "user": "string",
      "following": "string"
    }
**401**:
 

    {
    "detail": "Учетные данные не были предоставлены."
    }
### Получить JWT-токен
**Запрос**

    Post http://127.0.0.1:8000/api/v1/jwt/create/
    {
      "username": "string",
      "password": "string"
    }

**Ответ**

**200**:

    {
    "refresh": "string",
    "access": "string"
    }

**401**:
 
    {
    "detail": "No active account found with the given credentials"
    }
