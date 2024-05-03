## [REST API](http://localhost:8080/doc)

## Концепция:

- Spring Modulith
    - [Spring Modulith: достигли ли мы зрелости модульности](https://habr.com/ru/post/701984/)
    - [Introducing Spring Modulith](https://spring.io/blog/2022/10/21/introducing-spring-modulith)
    - [Spring Modulith - Reference documentation](https://docs.spring.io/spring-modulith/docs/current-SNAPSHOT/reference/html/)

```
  url: jdbc:postgresql://localhost:5432/jira
  username: jira
  password: JiraRush
```

- Есть 2 общие таблицы, на которых не fk
    - _Reference_ - справочник. Связь делаем по _code_ (по id нельзя, тк id привязано к окружению-конкретной базе)
    - _UserBelong_ - привязка юзеров с типом (owner, lead, ...) к объекту (таска, проект, спринт, ...). FK вручную будем
      проверять

## Аналоги

- https://java-source.net/open-source/issue-trackers

## Тестирование

- https://habr.com/ru/articles/259055/

___
## Запуск
Postgres DB
```
docker run -p 5432:5432 --name postgres-db -e POSTGRES_USER=jira -e POSTGRES_PASSWORD=JiraRush -v ./src/main/resources/pgdata:/var/lib/postgresql/data -d postgres
```
## [localhost:8080/](****)
## Список виконаних задач:

| №  | Done | Info                                                                                                    |
|:---|:-----|:--------------------------------------------------------------------------------------------------------|
| 1  | ✅| Розібратися зі структурою проєкту (onboarding)                                                          |
| 2  | ✅| Видалити соціальні мережі: vk, yandex.                                                                  |
| 3  | ✅| Винести чутливу інформацію до окремого проперті файлу **localhost.env**                                 |
| 4  | ✅| Тести на H2                                                                                             |
| 5  | ✅| Тести для всіх публічних методів контролера **ProfileRestController**                                   |
| 6  | ✅| Рефакторинг методу `com.javarush.jira.bugtracking.attachment.FileUtil#upload`                           |
| 7  | ✅| task_tag                                                                                                |
| 8  | ✅| підрахунок часу "**ACTIVITY**"  class:**TaskService**                                                   |
| 9  | ✅| Написати Dockerfile для основного сервера                                                               |
| 10 | ✅| Написати docker-compose файл для запуску контейнера сервера разом з БД та nginx.                        |
| 11 | ✅| Додати локалізацію. **En, Ru, Ua** файли: **index.html, email-confirmation.html,  password-reset.html** |
| 12 | ⛔️| **Переробити** механізм розпізнавання «свій-чужий» між фронтом і беком з JSESSIONID на JWT.             |
