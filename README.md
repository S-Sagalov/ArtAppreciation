## ArtAppreciation

Проект является бэкендом портала обзоров на различные произведения искусства, включающий систему публикации сведений о произведении, обзоров и комментариев к ним.
Включает в себя базу данных и открытый API.

<details>
<summary>Возможности API</summary>

- Администраторам: публиковать сведения о произведениях
- Получить сведения об оцениваемых произведениях
- Публиковать обзоры и рецензии
- Публиковать комментарии к обзорам и рецензиям
</details>

<details>
<summary>Примеры запросов</summary>

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
</details>

<details>
<summary>Запуск проекта локально</summary>

1) Клонировать репозиторий и перейти в папку "infra":

```
git clone git@github.com:S-Sagalov/ArtAppreciation.git
cd infra
```
2) Запустить сборку контейнеров:
```
docker-compose -up
```
3) Выполнить миграции:

```
docker-compose exec web python manage.py migrate
```

4) Создать суперпользователя:

```
docker-compose exec web python manage.py createsuperuser
```

5) Собрать файлы статики:

```
docker-compose exec web python3 manage.py collectstatic --no-input
```

6) Заполнить базу данными:

```
docker-compose exec web python manage.py loaddata fixtures.json 
```

</details>

<details>
<summary>Стек</summary>

- [![Python](https://img.shields.io/badge/Python-3.9-blue?style=flat-square&logo=Python&logoColor=3776AB&labelColor=d0d0d0)](https://www.python.org/)
- [![Django](https://img.shields.io/badge/Django-3.2-blue?style=flat-square&logo=Django&logoColor=3776AB&labelColor=d0d0d0)](https://docs.djangoproject.com/en/4.2/releases/3.2/)
- [![DRF](https://img.shields.io/badge/DRF-3.12.4-blue?style=flat-square&logoColor=3776AB&labelColor=d0d0d0)](https://www.django-rest-framework.org/community/release-notes/#3124)
- [![DRFSimpleJWT](https://img.shields.io/badge/DRF_SimpleJWT-3.12.4-blue?style=flat-square&logoColor=3776AB&labelColor=d0d0d0)](https://django-rest-framework-simplejwt.readthedocs.io/en/latest/)
- [![Docker](https://img.shields.io/badge/Docker-blue?style=flat-square&logo=Docker&logoColor=3776AB&labelColor=d0d0d0)](https://www.docker.com/)
</details>
