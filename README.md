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
###### Для MacOS DB:
```
docker run -p 5432:5432 --name postgres-db -e POSTGRES_USER=jira -e POSTGRES_PASSWORD=JiraRush -v ./src/main/resources/pgdata:/var/lib/postgresql/data -d postgres
docker run -p 5433:5432 --name postgres-db-test -e POSTGRES_USER=jira -e POSTGRES_PASSWORD=JiraRush -v ./src/test/resources/pgdata-test:/var/lib/postgresql/data -d postgres
```
- SDK 17
- Сбилдить <strong>mvn clean install</strong>
- Запустити Spring Boot програму (JiraRushApplication) з профілем **prod**


## Список виконаних задач:

| №  | Done | Info                                                                                                    |
|:---|:-----|:--------------------------------------------------------------------------------------------------------|
| 1  | ✅ | Розібратися зі структурою проєкту (onboarding)                                                          |
| 2  | ✅ | Видалити соціальні мережі: vk, yandex.                                                                  |
| 3  | ✅ | Винести чутливу інформацію до окремого проперті файлу **localhost.env**                                 |
| 4  | ✅ | Тести на H2                                                                                             |
| 5  | ✅ | Тести для всіх публічних методів контролера **ProfileRestController**                                   |
| 6  | ✅ | Рефакторинг методу `com.javarush.jira.bugtracking.attachment.FileUtil#upload`                           |
| 7  | ✅ | task_tag                                                                                                |
| 8  | ✅ | підрахунок часу "**ACTIVITY**"  class:**TaskService**                                                   |
| 9  |      |                                                                                                         |
| 10 |      |                                                                                                         |
| 11 | ✅ | Додати локалізацію. **En, Ru, Ua** файли: **index.html, email-confirmation.html,  password-reset.html** |
| 12 |      |                                                                                                         |

docker-compose up --build