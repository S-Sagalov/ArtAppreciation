## API для проекта YaTube

Проект является бэкендом портала обзоров на различные произведения искусства, включающий систему публикации сведений о произведении, обзоров и комментариев к ним.
Включает в себя базу данных и открытый API.

### API позволяет:
* Администраторам: публиковать сведения о произведениях
* Получить сведения об оцениваемых произведениях
* Публиковать обзоры и рецензии
* Публиковать комментарии к обзорам и рецензиям


### Примеры запросов:
Публикация обзора:
```
POST /api/v1/titles/{title_id}/reviews/
Тело: { "text": "Текст вашего обзора", "score": "оценка произведения" }
```
Просмотр обзоров:
```
GET /api/v1/titles/{title_id}/reviews/
Ответ:
{
  "count": 0,
  "next": "string",
  "previous": "string",
  "results": [
    {
      "id": 0,
      "text": "string",
      "author": "string",
      "score": 1,
      "pub_date": "2019-08-24T14:15:22Z"
    }
  ]
}
```
Публикация комментария:
```
POST /api/v1/titles/{title_id}/reviews/{review_id}/comments/
Тело: { "text": "Текст вашего комментария" }
```
Просмотр комментариев:
```
GET /api/v1/titles/{title_id}/reviews/{review_id}/comments/
Ответ:
{
  "count": 0,
  "next": "string",
  "previous": "string",
  "results": [
    {
      "id": 0,
      "text": "string",
      "author": "string",
      "pub_date": "2019-08-24T14:15:22Z"
    }
  ]
}
```

## Запуск проекта на сервере

1)Склонировать репозиторий:

```
git clone https://github.com/S-sagalov/yamdb_final.git
```

2)Выполнить вход на свой сервер

3)Установить docker на сервер:

```
sudo apt install docker.io
```

4)Установить docker-compose на сервер:

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

5)Запустить docker-compose:

```
docker-compose up -d --build
```

6)Собрать файлы статики, создать и выполнить миграции:

```
docker-compose exec web python3 manage.py makemigrations
```
```
docker-compose exec web python3 manage.py migrate
```
```
docker-compose exec web python3 manage.py collectstatic --no-input
```




### Использованные технологии:
* Django 3.2
* Django Rest Framework 3.12.4
* DRF SimpleJWT 4.7.2
* Docker
### Об авторе:
Студент кагорты 19+ ЯПрактикум
* Git - https://github.com/S-Sagalov

MIT License

![yamdb_workflow](https://github.com/S-Sagalov/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)