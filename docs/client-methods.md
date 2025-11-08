# Методы клиента

С сервисом Employee можно взаимодействовать через клиент. В этом файле — методы, они позволяют создавать, получать, изменять и выполнять другие действия с сущностями: сотрудниками `Person`, должностями `Position` и ролями `Role`.

> Подробнее о сущностях можно узнать в [_entities.md_](/docs/entities.md).

Ниже — список доступных методов:

## Для работы с сотрудниками

Методы для работы с сотрудниками (сущность `Person`):

| Метод | Описание | Параметры | Ответ |
|-------|----------|-----------|-------|
| `AddPerson(Guid user, PersonProps person)` | **[Устаревший]** Создание сотрудника | `user` — идентификатор пользователя <br> `person` — данные сотрудника | `EmployeeRequestResult<Guid>` |
| `SavePerson(Guid user, Person person)` | Создание или обновление сотрудника | `user` — идентификатор пользователя <br> `person` — данные сотрудника | `EmployeeRequestResult` |
| `GetPerson(Guid user, Guid personGuid)` | Получение сотрудника | `user` — идентификатор пользователя <br> `personGuid` — идентификатор сотрудника | `EmployeeRequestResult<Person>` |
| `GetPersons(Guid user, int? skip = null, int? take = null, IEnumerable<string> fieldsToInclude = null)` | Получение сотрудников | `user` — идентификатор пользователя <br> `skip` — сколько пропустить записей <br> `take` — сколько вернуть записей <br> `fieldsToInclude` — список полей, которые нужно включить | `EmployeeRequestResult<PersonsResponse>` |
| `DeletePerson(Guid user, Guid personGuid)` | Удаление сотрудника | `user` — идентификатор пользователя <br> `personGuid` — идентификатор сотрудника | `EmployeeRequestResult` |
| `SearchPersons(Guid user, IFilter filter, int? skip = null, int? take = null, IEnumerable<string> fieldsToInclude = null)` | Поиск сотрудников | `user` — идентификатор пользователя <br> `filter` — условия поиска <br> `skip` — сколько пропустить записей <br> `take` — сколько вернуть записей <br> `fieldsToInclude` — список полей, которые нужно включить | `EmployeeRequestResult<PersonsResponse>` |

---

## Для работы с должностями

Методы для работы с должностями (сущность `Position`):

| Метод | Описание | Параметры | Ответ |
|-------|----------|-----------|-------|
| `SavePosition(Guid user, Position position)` | Создание или обновление должности сотрудника | `user` — идентификатор пользователя <br> `position` — данные должности | `EmployeeRequestResult` |
| `GetPosition(Guid user, Guid person, Guid organization)` | Получение должности сотрудника | `user` — идентификатор пользователя <br> `person` — идентификатор сотрудника <br> `organization` — идентификатор организации | `EmployeeRequestResult<Position>` |

---

## Для работы с ролями

Методы для работы с ролями (сущность `Role`):

| Метод | Описание | Параметры | Ответ |
|-------|----------|-----------|-------|
| `SaveRole(Guid user, Role role)` | Создание или обновление роли сотрудника | `user` — идентификатор пользователя <br> `role` — данные роли | `EmployeeRequestResult` |
| `DeleteRole(Guid user, Guid organization, RoleType roleType)` | Удаление роли в организации | `user` — идентификатор пользователя <br> `organization` — идентификатор организации <br> `roleType` — тип роли | `EmployeeRequestResult` |
| `DeleteRoles(Guid user, Guid organization)` | Удаление всех ролей в организации | `user` — идентификатор пользователя <br> `organization` — идентификатор организации | `EmployeeRequestResult` |
| `GetRole(Guid user, Guid organization, RoleType roleType)` | Получение роли в организации | `user` — идентификатор пользователя <br> `organization` — идентификатор организации <br> `roleType` — тип роли | `EmployeeRequestResult<RoleResponse>` |
| `GetRoles(Guid user, Guid organization)` | Получение всех ролей в организации | `user` — идентификатор пользователя <br> `organization` — идентификатор организации | `EmployeeRequestResult<IReadOnlyDictionary<RoleType, RoleResponse>>` |
| `GetRoles(Guid user)` | Получение всех ролей во всех организациях | `user` — идентификатор пользователя | `EmployeeRequestResult<IReadOnlyDictionary<Guid, IReadOnlyDictionary<RoleType, RoleResponse>>>` |
| `GetPersonRoles(Guid user, Guid person, int? skip = null, int? take = null)` | Получение всех ролей сотрудника | `user` — идентификатор пользователя <br> `person` — идентификатор сотрудника <br> `skip` — сколько пропустить записей <br> `take` — сколько вернуть записей | `EmployeeRequestResult<IReadOnlyList<Role>>` |
