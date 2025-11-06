# Методы API

С сервисом Employee можно взаимодействовать через клиент `IEmployeeClient`, который оборачивает _REST API_. В этом файле описаны методы, которые позволяют создавать, получать, изменять и удалять сущности: сотрудников (`Person`), должности (`Position`) и роли (`Role`). Подробнее о том, какие есть сущности, можно прочитать в [_entities.md_](/docs/entities.md).

Ниже — список доступных методов по сущностям:

## `Person`

Методы для работы с сотрудниками:

| Метод | Описание | Параметры | Ответ |
|-------|----------|-----------|-------|
| `AddPerson(Guid user, PersonProps person)` | **[Устаревший]** Создание сотрудника. | `user`: Guid пользователя. <br> `person`: данные сотрудника. | `EmployeeRequestResult<Guid>` |
| `SavePerson(Guid user, Person person)` | Создание или обновление сотрудника. | `user`: Guid пользователя. <br> `person`: данные сотрудника. | `EmployeeRequestResult` |
| `GetPerson(Guid user, Guid personGuid)` | Получение сотрудника. | `user`: Guid пользователя. <br> `personGuid`: Guid сотрудника. | `EmployeeRequestResult<Person>` |
| `GetPersons(Guid user, int? skip = null, int? take = null, IEnumerable<string> fieldsToInclude = null)` | Получение сотрудников. | `skip`: сколько пропустить записей. <br> `take`: сколько вернуть записей. <br> `fieldsToInclude`: список полей, которые нужно включить. | `EmployeeRequestResult<PersonsResponse>` |
| `DeletePerson(Guid user, Guid personGuid)` | Удаление сотрудника. | `user`: Guid пользователя. <br> `personGuid`: Guid сотрудника. | `EmployeeRequestResult` |
| `SearchPersons(Guid user, IFilter filter, int? skip = null, int? take = null, IEnumerable<string> fieldsToInclude = null)` | Поиск сотрудников. | `filter`: фильтры. <br> `skip`: сколько пропустить записей. <br> `take`: сколько вернуть записей. <br> `fieldsToInclude`: список полей, которые нужно включить. | `EmployeeRequestResult<PersonsResponse>` |

---

## `Position`

Методы для работы с должностями:

| Метод | Описание | Параметры | Ответ |
|-------|----------|-----------|-------|
| `SavePosition(Guid user, Position position)` | Создание или обновление должности сотрудника. | `user`: Guid пользователя. <br> `position`: данные должности. | `EmployeeRequestResult` |
| `GetPosition(Guid user, Guid person, Guid organization)` | Получение должности сотрудника. | `user`: Guid пользователя. <br> `person`: Guid сотрудника. <br> `organization`: Guid организации. | `EmployeeRequestResult<Position>` |

---

## `Role`

Методы для работы с ролями:

| Метод | Описание | Параметры | Ответ |
|-------|----------|-----------|-------|
| `SaveRole(Guid user, Role role)` | Создание или обновление роли сотрудника. | `user`: Guid пользователя. <br> `role`: данные роли. | `EmployeeRequestResult` |
| `DeleteRole(Guid user, Guid organization, RoleType roleType)` | Удаление роли в организации. | `user`: Guid пользователя. <br> `organization`: Guid организации. <br> `roleType`: тип роли. | `EmployeeRequestResult` |
| `DeleteRoles(Guid user, Guid organization)` | Удаление всех ролей в организации. | `user`: Guid пользователя. <br> `organization`: Guid организации. | `EmployeeRequestResult` |
| `GetRole(Guid user, Guid organization, RoleType roleType)` | Получение роли в организации. | `user`: Guid пользователя. <br> `organization`: Guid организации. <br> `roleType`: тип роли. | `EmployeeRequestResult<RoleResponse>` |
| `GetRoles(Guid user, Guid organization)` | Получение всех ролей в организации. | `user`: Guid пользователя. <br> `organization`: Guid организации. | `EmployeeRequestResult<IReadOnlyDictionary<RoleType, RoleResponse>>` |
| `GetRoles(Guid user)` | Получение всех ролей во всех организациях. | `user`: Guid пользователя. | `EmployeeRequestResult<IReadOnlyDictionary<Guid, IReadOnlyDictionary<RoleType, RoleResponse>>>` |
| `GetPersonRoles(Guid user, Guid person, int? skip = null, int? take = null)` | Получение всех ролей сотрудника. | `user`: Guid пользователя. <br> `person`: Guid сотрудника. <br> `skip`: сколько пропустить записей. <br> `take`: сколько вернуть записей. | `EmployeeRequestResult<IReadOnlyList<Role>>` |

