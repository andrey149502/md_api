# Управление графиками активности

**ДОСТУПНО КЛИЕНТАМ**

> Нужно добавить отдельные методы управления рабочими расписаниями и временем активности


## Получение списка графиков активности

Метод | `get.schedules`
:---- | :------------
Версия API | v2
Описание | Получение списка графиков активности
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов


### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел **"Критерии фильтрации"**
`fields` | array | нет |  | См. раздел **"Представление возвращаемых данных"**
`sort` | array | нет |  | См. раздел **"Сортировка данных"**


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
			<td><code>id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор графика активности</td>
		</tr>
		<tr>
			<td><code>name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>Название графика активности</td>
		</tr>
		<tr>
			<td colspan="6">Расписания работы</td>
		</tr>
		<tr>
			<td><code>schedules</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>Расписания работы</td>
		</tr>
		<tr>
			<td><code>activity_days</code></td>
			<td>object</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Дни в которые график активен</td>
		</tr>
		<tr>
			<td><code>type</code></td>
			<td>enum</td>
			<td>
				<code>days_of_week</code>,<br>
				<code>days_of_month</code>
			</td>
			<td></td>
			<td></td>
			<td>Тип. По дням недели или по числам месяца.</td>
		</tr>
		<tr>
			<td><code>days</code></td>
			<td>array</td>
			<td>
				Если <code>"type" = "days_of_week"</code>:
				<ul>
					<li>1 - понедельник;</li>
					<li>2 - вторник;</li>
					<li>3 - среда;</li>
					<li>4 - четверг;</li>
					<li>5 - пятница;</li>
					<li>6 - суббота</li>
					<li>0 - воскресенье;</li>
					<li>8 - выходной;</li>
					<li>7 - рабочий;</li>
				</ul>
				Если <code>"type" = "days_of_month"</code>:
				<ul>
					<li>числа от 1 до 31</li>
				</ul>
			</td>
			<td></td>
			<td></td>
			<td>Дни недели или месяца</td>
		</tr>
		<tr>
			<td colspan="6">Время активности графика</td>
		</tr>
		<tr>
			<td><code>activity_time</code></td>
			<td>array</td>
			<td></td>
			<td></td>
			<td></td>
			<td>
				Время активности графика.
				<blockquote>
					Если параметр не задан, то график работает
					без ограничений
				</blockquote>
			</td>
		</tr>
		<tr>
			<td><code>time_from</code></td>
			<td>string</td>
			<td>HH:MM</td>
			<td></td>
			<td></td>
			<td>Время начала активности графика</td>
		</tr>
		<tr>
			<td><code>time_till</code></td>
			<td>string</td>
			<td>HH:MM</td>
			<td></td>
			<td></td>
			<td>
				Время окончания активности графика.
				<br><br>
				Должно быть обязательно больше чем указано в параметре <code>"time_from"</code>
			</td>
		</tr>
		<tr>
			<td colspan="6">Период активности графика</td>
		</tr>
		<tr>
			<td><code>activity_date_from</code></td>
			<td>string</td>
			<td>YYYY-MM-DD</td>
			<td></td>
			<td></td>
			<td>Дата начала активности графика</td>
		</tr>
		<tr>
			<td><code>activity_date_till</code></td>
			<td>string</td>
			<td>YYYY-MM-DD</td>
			<td></td>
			<td></td>
			<td>Дата окончания активности графика</td>
		</tr>
	</tbody>
</table>


### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.schedules",
  "params":{
    "access_token":"string",
    "user_id":"number",
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
        "schedules":[
          {
            "activity_days":{
              "type":"enum",
              "days":[

              ]
            },
            "activity_time":[
              {
                "time_from":"string",
                "time_till":"string"
              }
            ],
            "activity_date_from":"string",
            "activity_date_till":"string"
          }
        ]
      }
    ]
  }
}
```


### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом get](#)"



## Создание графика активности

Метод | `create.schedules`
:---- | :---------------
Версия API | v2
Описание | Создание графика активности
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов


### Параметры запроса

<table>
	<tbody>
		<tr>
			<th>Название</th>
			<th>Тип</th>
			<th>Обязательный</th>
			<th>Допустимые значения</th>
			<th>Описание</th>
		</tr>
		<tr>
			<td><code>access_token</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Ключ сессии аутентификации</td>
		</tr>
		<tr>
			<td><code>user_id</code></td>
			<td>number</td>
			<td>нет</td>
			<td></td>
			<td>
				Уникальный идентификатор пользователя клиента агента от имени которого делается запрос
				<blockquote>Является обязательным для агента</blockquote>
			</td>
		</tr>
		<tr>
			<td><code>name</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>
				Название графика активности
			</td>
		</tr>
		<tr>
			<td colspan="5">Расписания работы</td>
		</tr>
		<tr>
			<td><code>schedules</code></td>
			<td>array</td>
			<td>да</td>
			<td></td>
			<td>Расписания работы</td>
		</tr>
		<tr>
			<td><code>activity_days</code></td>
			<td>object</td>
			<td>да</td>
			<td></td>
			<td>Дни в которые график активен</td>
		</tr>
		<tr>
			<td><code>type</code></td>
			<td>enum</td>
			<td>да</td>
			<td>
				<code>days_of_week</code>,<br>
				<code>days_of_month</code>
			</td>
			<td>Тип. По дням недели или по числам месяца.</td>
		</tr>
		<tr>
			<td><code>days</code></td>
			<td>array</td>
			<td>да</td>
			<td>
				Если <code>"type" = "days_of_week"</code>:
				<ul>
					<li>1 - понедельник;</li>
					<li>2 - вторник;</li>
					<li>3 - среда;</li>
					<li>4 - четверг;</li>
					<li>5 - пятница;</li>
					<li>6 - суббота</li>
					<li>0 - воскресенье;</li>
					<li>8 - выходной;</li>
					<li>7 - рабочий;</li>
				</ul>
				Если <code>"type" = "days_of_month"</code>:
				<ul>
					<li>числа от 1 до 31</li>
				</ul>
			</td>
			<td>Дни недели или месяца</td>
		</tr>
		<tr>
			<td colspan="5">Время активности графика</td>
		</tr>
		<tr>
			<td><code>activity_time</code></td>
			<td>array</td>
			<td>нет</td>
			<td></td>
			<td>
				Время активности графика.
				<blockquote>
					Если параметр не задан, то график работает
					без ограничений
				</blockquote>
			</td>
		</tr>
		<tr>
			<td><code>time_from</code></td>
			<td>string</td>
			<td>да</td>
			<td>HH:MM</td>
			<td>Время начала активности графика</td>
		</tr>
		<tr>
			<td><code>time_till</code></td>
			<td>string</td>
			<td>да</td>
			<td>HH:MM</td>
			<td>
				Время окончания активности графика.
				<br><br>
				Должно быть обязательно больше чем указано в параметре <code>"time_from"</code>
			</td>
		</tr>
		<tr>
			<td colspan="5">Период активности графика</td>
		</tr>
		<tr>
			<td><code>activity_date_from</code></td>
			<td>string</td>
			<td>нет</td>
			<td>YYYY-MM-DD</td>
			<td>Дата начала активности графика</td>
		</tr>
		<tr>
			<td><code>activity_date_till</code></td>
			<td>string</td>
			<td>нет</td>
			<td>YYYY-MM-DD</td>
			<td>Дата окончания активности графика</td>
		</tr>
	</tbody>
</table>


### Параметры ответа

Название | Имена в БД | Тип | Обязательный | Допустимые значения | Описание
-------- | ---------- | --- | ------------ | ------------------- | --------
`id` |  | number | да |  | Уникальный идентификатор графика активности


### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"create.schedules",
  "params":{
    "access_token":"string",
    "id":"number",
    "name":"string",
    "schedules":[
      {
        "activity_days":{
          "type":"enum",
          "days":[

          ]
        },
        "activity_time":[
          {
            "time_from":"string",
            "time_till":"string"
          }
        ],
        "activity_date_from":"string",
        "activity_date_till":"string"
      }
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



## Удаление графика активности

Метод | `delete.schedules`
:---- | :------------
Версия API | v2
Описание | Удаление графика активности
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов


### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`id` | number | да |  | Уникальный идентификатор графика активности
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>


### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"delete.schedules",
  "params":{
    "access_token":"string",
    "id":"number",
    "user_id":"number"
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

Смотрим раздел "[Список ошибок для методов с глаголом delete](#)"



## Редактирование графика активности

Метод | `update.schedules`
:---- | :------------
Версия API | v2
Описание | Редактирование графика активности
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов


### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`id` | number | да |  | Уникальный идентификатор графика активности
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`name` | string | да |  | Название графика активности


### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"update.schedules",
  "params":{
    "access_token":"string",
    "id":"number",
    "user_id":"number",
    "name":"string"
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
