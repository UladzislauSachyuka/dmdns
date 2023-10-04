# Модели данных и системы управления базами данных
## Сачивко Владислав, 153502
Тема: Косметологический центр

### Функциональные требования:

1. Авторизация пользователя, личный кабинет.
2. Управление пользователями (CRUD).
3. Система ролей (клиент, доктор, администратор).
4. Для всех:
   * Просмотр основной информации об услугах, врачах. Просмотр отзывов.
6. Для клиента:
   * Запись к врачу на оказание услуги (и её отмена).
   * Возможность оставить отзыв о качестве оказанной услуги и о центре в целом.
7. Для доктора:
   * Просмотр своего расписания.
   * Составление своего расписания.
8. Для администратора:
   * Просмотр продаж.
   * Просмотр истории посещений.
   
### Описание сущностей:
1. "Role":
    * "id" BIGINT NOT NULL, PK
    * "name" VARCHAR NOT NULL
2. "User":
    * "id" BIGINT NOT NULL, PK
    * "name" VARCHAR NOT NULL
    * "role_id" BIGINT NOT NULL -> Role, FK
    * "login" VARCHAR NOT NULL
    * "password" VARCHAR NOT NULL
3. "Doctor":
    * "id" BIGINT NOT NULL, PK
    * "user_id" BIGINT NOT NULL -> User, FK
    * "category_id" BIGINT NOT NULL -> Category, FK 
4. "Client":
    * "id" BIGINT NOT NULL, PK
    * "user_id" BIGINT NOT NULL -> User, FK
    * "birthdate" DATE NOT NULL
    * "address" VARCHAR NOT NULL
5. "Category":
    * "id" BIGINT NOT NULL, PK
    * "name" VARCHAR NOT NULL
6. "Office":
    * "id" BIGINT NOT NULL, PK
    * "number" INT NOT NULL
7. "Service":
    * "id" BIGINT NOT NULL, PK
    * "name" VARCHAR NOT NULL
    * "price" INT NOT NULL
8. "Schedule":
    * "id" BIGINT NOT NULL, PK
    * "doctor_id" BIGINT NOT NULL -> Doctor, FK
    * "client_id" BIGINT NOT NULL -> Client, FK
    * "office_id" BIGINT NOT NULL -> Office, FK
    * "date" date NOT NULL
9. "Sale":
    * "id" BIGINT NOT NULL, PK
    * "service_id" BIGINT NOT NULL -> Service, FK
    * "doctor_id" BIGINT NOT NULL -> Doctor, FK
    * "client_id" BIGINT NOT NULL -> Client, FK
    * "date" DATE NOT NULL
10. "Review":
    * "id" BIGINT NOT NULL, PK
    * "client_id" BIGINT NOT NULL -> Client, FK
    * "content" VARCHAR NOT NULL
    * "mark" INT NOT NULL
    * "date" DATE NOT NULL
11. "Log":
    * "id" BIGINT NOT NULL, PK
    * "action" VARCHAR NOT NULL
    * "user_id" BIGINT NOT NULL -> User, FK
    * "datetime" DATETIME NOT NULL
