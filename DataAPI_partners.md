# [Агенты] Управление клиентами

**ДОСТУПНО КЛИЕНТАМ**

> Должна быть проверка принадлежности клиента партнёру

> агентам доступны так же методы клиентов

## Получение клиентов агента

Метод | `get.customers`
:---- | :---------------
Версия API | v2
Описание | Получение клиентов агента
Кому доступен | Партнёр
Ссылка | Вернуться к списку методов

> Архивные клиенты не отображаются в выводе

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"

### Параметры ответа

<table>
	<tbody>
		<tr>
			<th>Название</th>
			<th>Тип</th>
			<th>Допустимые значения</th>
			<th>Фильтрация</th>
			<th>Сортировка</th>
			<th>Описание</th>
		</tr>
		<tr>
			<td>`id`</td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор клиента</td>
		</tr>
		<tr>
			<td>`name`</td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>Название клиента</td>
		</tr>
		<tr>
			<td>`description`</td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Описание к клиенту</td>
		</tr>
		<tr>
			<td>`creation_date_time`</td>
			<td>iso8601</td>
			<td>YYYY-MM-DD
hh:mm:ss</td>
			<td></td>
			<td>да</td>
			<td>Дата и время создания клиента</td>
		</tr>
		<tr>
			<td>`status`</td>
			<td>enum</td>
			<td>
				<ul>
					<li>`waiting`</li>
					<li>`active`</li>
					<li>`manual_lock`</li>
					<li>`limit_lock`</li>
					<li>`debt_lock`</li>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td>Статус клиента</td>
		</tr>
		<tr>
			<td>`status_change_date_time`</td>
			<td>iso8601</td>
			<td>YYYY-MM-DD
hh:mm:ss</td>
			<td></td>
			<td></td>
			<td>Дата и время изменения статуса</td>
		</tr>
		<tr>
			<td>`monthly_base_limit`</td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Общий месячный лимит. Значение задаётся в
деньгах.</td>
		</tr>
		<tr>
			<td>`monthly_base_notify_limit`</td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Пороговое значение общего месячного лимита при
достижению которого отправляется уведомление на
электронный адрес указанный в параметре
`"monthly_base_notify_email"`</td>
		</tr>
		<tr>
			<td>`monthly_base_notify_emails`</td>
			<td>array</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Адреса электронной почты для получения
уведомлений о достижении общего месячного
лимита</td>
		</tr>
		<tr>
			<td>`monthly_calls_limit`</td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Месячный лимит по звонкам. Значение задаётся в
количестве звонков.</td>
		</tr>
		<tr>
			<td>`monthly_calls_notify_limit`</td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Пороговое значение месячного лимита по звонкам
при достижению которого отправляется
уведомление на электронный адрес указанный в
параметре `"monthly_calls_notify_email"`</td>
		</tr>
		<tr>
			<td>`monthly_calls_notify_emails`</td>
			<td>array</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Адреса электронной почты для получения
уведомлений о достижении месячного лимита по
звонкам</td>
		</tr>
		<tr>
			<td>`daily_calls_limit`</td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Дневной лимит по звонкам. Значение задаётся в
количестве звонков.</td>
		</tr>
		<tr>
			<td>`daily_calls_notify_limit`</td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>
				Пороговое значение дневного лимита по звонкам
при достижению которого отправляется
уведомление на электронный адрес указанный в
параметре `"daily_calls_notify_email"`
			</td>
		</tr>
		<tr>
			<td>`daily_calls_notify_emails`</td>
			<td>array</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Адреса электронной почты для получения
уведомлений о достижении дневного лимита по
звонкам</td>
		</tr>
		<tr>
			<td colspan="6">Список сайтов клиента</td>
		</tr>
		<tr>
			<td>`sites`</td>
			<td>array</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Список сайтов клиента</td>
		</tr>
		<tr>
			<td>`site_id`</td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный индентификатор сайта</td>
		</tr>
		<tr>
			<td>`site_domain_name`</td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Доменное имя сайта</td>
		</tr>
		<tr>
			<td colspan="6">Тарифный план</td>
		</tr>
		<tr>
			<td>`tariff_plan_id`</td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор тарифного плана</td>
		</tr>
		<tr>
			<td>`tariff_plan_name`</td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>Название тарифного плана</td>
		</tr>
	</tbody>
</table>

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.customers",
  "params":{
    "access_token":"string",
    "offset":"number",
    "limit":"number",
    "filter":{

    },
    "sort":[
      {
        "field":"string",
        "order":"string"
      }
    ],
    "fields":[
      "string"
    ]
  }
}
```

### JSON структура ответа

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "result":{
    "metadata":{

    },
    "data":[
      {
        "id":"number",
        "name":"string",
        "description":"string",
        "creation_date_time":"iso8601",
        "status":"enum",
        "status_change_date_time":"iso8601",
        "tariff_plan_id":"number",
        "tariff_plan_name":"string",
        "monthly_base_limit":"number",
        "monthly_base_notify_limit":"number",
        "monthly_base_notify_emails":[
          "item"
        ],
        "monthly_calls_limit":"number",
        "monthly_calls_notify_limit":"number",
        "monthly_calls_notify_emails":[
          "item"
        ],
        "daily_calls_limit":"number",
        "daily_calls_notify_limit":"number",
        "daily_calls_notify_emails":[
          "item"
        ],
        "sites":[
          {
            "site_domain_name":"string",
            "site_id":"number"
          }
        ]
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом get](#)"


## Создание клиента агента

Метод | `create.customers`
:---- | :---------------
Версия API | v2
Описание | Создание клиента агента
Кому доступен | Партнёр
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`name` | string | да |  | Название клиента
`description` | string | нет |  | Описание к клиенту
`tariff_plan_id` | number | да |  | Уникальный идентификатор тарифного плана. Список доступных тарифных планов можно получить с помощью метода `"get.partner_tariffs"`
`email` | string | да |  | Адрес электронной почты клиента
`password` | string | да | Минимальная длина 8 символов | Пароль для клиента
`monthly_base_limit` | number | нет |  | Общий месячный лимит. Значение задаётся в деньгах.
`monthly_base_notify_limit` | number | нет |  | Пороговое значение общего месячного лимита при достижению которого отправляется уведомление на электронный адрес указанный в параметре `"monthly_base_notify_email"`
`monthly_base_notify_emails` | array | да | Максимум 5 адресов | Адреса электронной почты для получения уведомлений о достижении общего месячного лимита
`monthly_calls_limit` | number | нет |  | Месячный лимит по звонкам. Значение задаётся в количестве звонков.
`monthly_calls_notify_limit` | number | нет |  | Пороговое значение месячного лимита по звонкам при достижению которого отправляется уведомление на электронный адрес указанный в параметре `"monthly_calls_notify_email"`
`monthly_calls_notify_emails` | array | да | Максимум 5 адресов | Адреса электронной почты для получения уведомлений о достижении месячного лимита по звонкам
`daily_calls_limit` | number | нет |  | Дневной лимит по звонкам. Значение задаётся в количестве звонков.
`daily_calls_notify_limit` | number | нет |  | Пороговое значение дневного лимита по звонкам при достижению которого отправляется уведомление на электронный адрес указанный в параметре `"daily_calls_notify_email"`
`daily_calls_notify_emails` | array | да | Максимум 5 адресов | Адреса электронной почты для получения уведомлений о достижении дневного лимита по звонкам

### Параметры ответа

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`id` | number | да |  | Уникальный идентификатор клиента

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"create.customers",
  "params":{
    "access_token":"string",
    "name":"string",
    "description":"string",
    "tariff_plan_id":"number",
    "email":"string",
    "password":"string",
    "monthly_base_limit":"number",
    "monthly_base_notify_limit":"number",
    "monthly_base_notify_emails":[
      "item"
    ],
    "monthly_calls_limit":"number",
    "monthly_calls_notify_limit":"number",
    "monthly_calls_notify_emails":[
      "item"
    ],
    "daily_calls_limit":"number",
    "daily_calls_notify_limit":"number",
    "daily_calls_notify_emails":[
      "item"
    ]
  }
}
```

### JSON структура ответа

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "result":{
    "id":"number"
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом create](#)"


## Редактирование параметров клиента агента

Метод | `update.customers`
:---- | :---------------
Версия API | v2
Описание | Редактирование параметров клиента агента
Кому доступен | Партнёр
Ссылка | Вернуться к списку методов

> Возможно частичное обновление. Если обновляется массив данных, то переданный массив будет полностью заменять существующий.

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`id` | number | да |  | Уникальный идентификатор клиента
`name` | string | да |  | Название клиента
`description` | string | нет |  | Описание к клиенту
`monthly_base_limit` | number | нет |  | Общий месячный лимит. Значение задаётся в деньгах.
`monthly_base_notify_limit` | number | нет |  | Пороговое значение общего месячного лимита при достижению которого отправляется уведомление на электронный адрес указанный в параметре `"monthly_base_notify_email"`
`monthly_base_notify_emails` | array | да | Максимум 5 адресов | Адреса электронной почты для получения уведомлений о достижении общего месячного лимита
`monthly_calls_limit` | number | нет |  | Месячный лимит по звонкам. Значение задаётся в количестве звонков.
`monthly_calls_notify_limit` | number | нет |  | Пороговое значение месячного лимита по звонкам при достижению которого отправляется уведомление на электронный адрес указанный в параметре `"monthly_calls_notify_email"`
`monthly_calls_notify_emails` | array | да | Максимум 5 адресов | Адреса электронной почты для получения уведомлений о достижении месячного лимита по звонкам
`daily_calls_limit` | number | нет |  | Дневной лимит по звонкам. Значение задаётся в количестве звонков.
`daily_calls_notify_limit` | number | нет |  | Пороговое значение дневного лимита по звонкам при достижению которого отправляется уведомление на электронный адрес указанный в параметре `"daily_calls_notify_email"`
`daily_calls_notify_emails` | array | да | Максимум 5 адресов | Адреса электронной почты для получения уведомлений о достижении дневного лимита по звонкам

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"update.customers",
  "params":{
    "access_token":"string",
    "id":"number",
    "name":"string",
    "description":"string",
    "monthly_base_limit":"number",
    "monthly_base_notify_limit":"number",
    "monthly_base_notify_emails":[
      "item"
    ],
    "monthly_calls_limit":"number",
    "monthly_calls_notify_limit":"number",
    "monthly_calls_notify_emails":[
      "item"
    ],
    "daily_calls_limit":"number",
    "daily_calls_notify_limit":"number",
    "daily_calls_notify_emails":[
      "item"
    ]
  }
}
```

### JSON структура ответа

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "result":{

  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом update](#)"


## Изменение статуса клиента агента

Метод | `update.customer_status`
:---- | :---------------
Версия API | v2
Описание | Изменение статуса клиента агента
Кому доступен | Партнёр
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`customer_id` | number | да |  | Уникальный идентификатор клиента
`status` | enum | да | `active`, `archive`, `manual_lock` | Новый статус.<br><br>Активировать можно только клиента который находятся в статусе `"waiting"`.<br><br>Заблокировать возможно только клиента который находится в статусе `"active"`.<br><br>Архивировать можно только клиента который находится в статусе `"manual_lock"`<br><br>Разблокировать можно только клиента который находится в статусе `"manual_lock"`

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"update.customer_status",
  "params":{
    "access_token":"string",
    "customer_id":"number",
    "status":"enum"
  }
}
```

### JSON структура ответа

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "result":{

  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом update](#)"
+

Текст | Код  | Мнемоника | Описание
:---- | :--- | :-------- | :-------
```An attempt was made to use a status that is not correct in this state``` | -32602 | `invalid_state` | Указанный статус некорректен для клиента в текущем состоянии


## Смена тарифного плана у клиента агента

Метод | `update.customer_tariff_plans`
:---- | :---------------
Версия API | v2
Описание | Смена тарифного плана у клиента агента
Кому доступен | Партнёр
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`customer_id` | number | да |  | Уникальный идентификатор клиента
`tariff_plan_id` | number | да |  | Уникальный идентификатор тарифного плана. Список доступных тарифных планов можно получить с помощью метода `"get.tariff_plans"`

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"update.customer_tariff_plans",
  "params":{
    "access_token":"string",
    "customer_id":"number",
    "tariff_plan_id":"number"
  }
}
```

### JSON структура ответа

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "result":{

  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом update](#)"


## Получение доступных тарифных планов агента

Метод | `get.tariff_plans`
:---- | :---------------
Версия API | v2
Описание | Получение доступных тарифных планов агента
Кому доступен | Агент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"`` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел **"Критерии фильтрации"**
`fields` | array | нет |  | См. раздел **"Представление возвращаемых данных"**
`sort` | array | нет |  | См. раздел **"Сортировка данных"**

### Параметры ответа

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`id` | number | да |  | Уникальный идентификатор тарифного плана
`name` | string | да |  | Название тарифного плана

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.tariff_plans",
  "params":{
    "access_token":"string",
    "offset":"number",
    "limit":"number",
    "filter":{

    },
    "sort":[
      {
        "field":"string",
        "order":"string"
      }
    ],
    "fields":[
      "string"
    ]
  }
}
```

### JSON структура ответа

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "result":{
    "metadata":{

    },
    "data":[
      {
        "id":"number",
        "name":"string"
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом get](#)"


## Получение списка пользователей клиента для API запросов

Метод | `get.customer_users`
:---- | :---------------
Версия API | v2
Описание | Получение списка пользователей клиента из под которых можно совершать API запросы
Кому доступен | Партнёр
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел **"Критерии фильтрации"**
`fields` | array | нет |  | См. раздел **"Представление возвращаемых данных"**
`sort` | array | нет |  | См. раздел **"Сортировка данных"**

### Параметры ответа

Название | Тип  | Допустимые значения | Фильтрация | Сортировка | Описание
:------- | :--- | :------------------ | :--------- | :--------- | :-------
`id` | number |  | да |  | Уникальный идентификатор пользователя <blockquote>Используется как user_id во всех клиентских методах</blockquote>
`login` | string |  |  |  | Логин пользователя
`description` | string |  |  |  | Описание пользователя
`name` | string |  | да | да | Имя пользователя
`customer_id` | number |  | да | да | Уникальный идентификатор клиента

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.customer_users",
  "params":{
    "access_token":"string",
    "offset":"number",
    "limit":"number",
    "filter":{

    },
    "sort":[
      {
        "field":"string",
        "order":"string"
      }
    ],
    "fields":[
      "string"
    ]
  }
}
```

### JSON структура ответа

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "result":{
    "metadata":{

    },
    "data":[
      {
        "id":"number",
        "name":"string",
        "description":"string",
        "login":"string",
        "customer_id":"number"
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом get](#)"