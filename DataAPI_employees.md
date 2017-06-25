# Управление сотрудниками

**БД:** `DONE`

**Python:** `DONE`

## Получение списка сотрудников

Метод | `get.employees`
:---- | :---------------
Версия API | v2
Описание | Получение списка сотрудников
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать <code>"limit"</code> записей. По умолчанию <code>"0"</code>.
`filter` | object | нет |  | См. раздел **"Критерии фильтрации"**
`fields` | array | нет |  | См. раздел **"Представление возвращаемых данных"**
`sort` | array | нет |  | См. раздел **"Сортировка данных"**

### Параметры ответа

<table>
	<thead>
		<tr>
			<th align="left">Название</th>
			<th align="left">Тип</th>
			<th align="left">Допустимые значения</th>
			<th align="left">Фильтрация</th>
			<th align="left">Сортировка</th>
			<th align="left">Описание</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td align="left"><code>id</code></td>
			<td align="left">number</td>
			<td align="left"></td>
			<td align="left">да</td>
			<td align="left"></td>
			<td align="left">Уникальный идентификатор сотрудника</td>
		</tr>
		<tr>
			<td align="left"><code>first_name</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left">да</td>
			<td align="left">да</td>
			<td align="left">Имя сотрудника</td>
		</tr>
		<tr>
			<td align="left"><code>last_name</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left">да</td>
			<td align="left">да</td>
			<td align="left">Фамилия сотрудника</td>
		</tr>
		<tr>
			<td align="left"><code>patronymic</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">да</td>
			<td align="left">Отчество сотрудника</td>
		</tr>
		<tr>
			<td align="left"><code>full_name</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left">да</td>
			<td align="left">да</td>
			<td align="left">Фамилия Имя Отчество</td>
		</tr>
		<tr>
			<td align="left"><code>email</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left">да</td>
			<td align="left"></td>
			<td align="left">Адрес электронной почты сотрудника</td>
		</tr>
		<tr>
			<td align="left"><code>call_recording</code></td>
			<td align="left">enum</td>
			<td align="left">
				<ul>
					<li><code>all</code> - для всех звонков;</li>
					<li><code>in</code> - только для входящих;</li>
					<li><code>out</code> - только для исходящих;</li>
					<li><code>off</code> - отключена</li>
				</ul>
			</td>
			<td align="left">да</td>
			<td align="left"></td>
			<td align="left">Статус записи разговоров</td>
		</tr>
		<tr>
			<td align="left"><code>calls_available</code></td>
			<td align="left">boolean</td>
			<td align="left"><code>true</code>, <code>false</code></td>
			<td align="left">да</td>
			<td align="left">да</td>
			<td align="left">Доступность для звонков</td>
		</tr>
		<tr>
			<td align="left"><code>schedule_id</code></td>
			<td align="left">number</td>
			<td align="left"></td>
			<td align="left">да</td>
			<td align="left"></td>
			<td align="left">Уникальный идентификатор графика активности</td>
		</tr>
		<tr>
			<td align="left"><code>schedule_name</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left">да</td>
			<td align="left"></td>
			<td align="left">Название графика активности</td>
		</tr>
		<tr>
			<td align="left" colspan="6">Тренер</td>
		</tr>
		<tr>
			<td align="left"><code>coach</code></td>
			<td align="left">object</td>
			<td align="left"></td>
			<td align="left">да</td>
			<td align="left"></td>
			<td align="left">Тренер для сотрудника</td>
		</tr>
		<tr>
			<td align="left"><code>coach_full_name</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Ф.И.О тренера</td>
		</tr>
		<tr>
			<td align="left"><code>coach_id</code></td>
			<td align="left">number</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Уникальный идентификатор тренера <blockquote>Выбирается из списка сотрудников</blockquote></td>
		</tr>
		<tr>
			<td align="left"><code>coach_always_enabled</code></td>
			<td align="left">boolean</td>
			<td align="left"><code>true</code>, <code>false</code></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">При активации опции все входящие звонки сотрудника будут дублироваться его тренеру.</td>
		</tr>
		<tr>
			<td align="left" colspan="6">Группы сотрудника</td>
		</tr>
		<tr>
			<td align="left"><code>groups</code></td>
			<td align="left">array</td>
			<td align="left"></td>
			<td align="left">да</td>
			<td align="left"></td>
			<td align="left">Группы вкоторых состоит сотрудник</td>
		</tr>
		<tr>
			<td align="left"><code>group_id</code></td>
			<td align="left">number</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Уникальный идентификатор группы</td>
		</tr>
		<tr>
			<td align="left"><code>group_name</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Название группы</td>
		</tr>
		<tr>
			<td align="left" colspan="6">Телефоны</td>
		</tr>
		<tr>
			<td align="left"><code>phone_numbers</code></td>
			<td align="left">array</td>
			<td align="left">10 штук</td>
			<td align="left">да</td>
			<td align="left"></td>
			<td align="left">Список телефонов сотрудника. <blockquote>Список номеров должен быть отсортирован по приоритету.</blockquote></td>
		</tr>
		<tr>
			<td align="left"><code>phone_number</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">
				Номер телефона сотрудника. Формат номера
				может быть с донабором, к примеру
				<code>"74955140578...2345"</code>, поэтому у номера не
				формат E164
				<blockquote>
					Если указан SIP, то не делаем
					связки, а просто добавляем как
					номер типа ТФОП, т.е. как обычный
					номер
				</blockquote>	
			</td>
		</tr>
		<tr>
			<td align="left"><code>channels_count</code></td>
			<td align="left">number</td>
			<td align="left">От 1 до 30</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Значение по умолчанию <code>"1"</code>. Количество
линий на телефоне</td>
		</tr>
		<tr>
			<td align="left"><code>dial_time</code></td>
			<td align="left">number</td>
			<td align="left">От 1 до 100</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Значение по умолчанию <code>"60"</code>. Время дозвона
по телефону. Значение в секундах.</td>
		</tr>
		<tr>
			<td align="left"><code>status</code></td>
			<td align="left">enum</td>
			<td align="left"><code>active</code>, <code>inactive</code></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Значение по умолчанию <code>"active"</code>. Статус
номера.</td>
		</tr>
		<tr>
			<td align="left" colspan="6">Внутренний номер</td>
		</tr>
		<tr>
			<td align="left"><code>extension</code></td>
			<td align="left">object</td>
			<td align="left"></td>
			<td align="left">да</td>
			<td align="left"></td>
			<td align="left">Внутренний номер и его настройки</td>
		</tr>
		<tr>
			<td align="left"><code>extension_phone_number</code></td>
			<td align="left">string</td>
			<td align="left">Максимальная
длина 4</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Внутренний номер</td>
		</tr>
		<tr>
			<td align="left"><code>extension_voice_mail_enabled</code></td>
			<td align="left">boolean</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">В случае, если все номера, указанные для
этого сотрудника в списке телефонов,
заняты, то звонящему абоненту будет
предложено оставить голосовое сообщение.</td>
		</tr>
		<tr>
			<td align="left"><code>extension_queue_enabled</code></td>
			<td align="left">boolean</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">В случае, если все номера, указанные для
этого сотрудника в списке телефонов,
заняты, то звонящий абонент встанет в
очередь на повторный дозвон до телефонов
в списке и будет ждать первый
освободившийся номер.</td>
		</tr>
		<tr>
			<td align="left" colspan="6">Сотрудник является оператором чата</td>
		</tr>
		<tr>
			<td align="left"><code>operator</code></td>
			<td align="left">object</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Оператор рабочего места</td>
		</tr>
		<tr>
			<td align="left"><code>operator_login</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Логин оператора для входа в приложение
«Рабочее место оператора»</td>
		</tr>
		<tr>
			<td align="left"><code>operator_position_id</code></td>
			<td align="left">number</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Уникальный идентификатор должности
оператора в подписи</td>
		</tr>
		<tr>
			<td align="left"><code>operator_position_name</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Название должности оператора в подписи</td>
		</tr>
		<tr>
			<td align="left"><code>operator_offline_message_enabled</code></td>
			<td align="left">boolean</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Разрешено ли обрабатывать заявки</td>
		</tr>
		<tr>
			<td align="left"><code>operator_invite_to_chat_enabled</code></td>
			<td align="left">boolean</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Разрешено ли приглашать в чат</td>
		</tr>
		<tr>
			<td align="left"><code>operator_chat_enabled</code></td>
			<td align="left">boolean</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Разрешено ли участвовать в чатах с посетителями</td>
		</tr>
		<tr>
			<td align="left"><code>operator_chats_available</code></td>
			<td align="left">boolean</td>
			<td align="left"><code>true</code>, <code>false</code></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Доступность для чатов</td>
		</tr>
		<tr>
			<td align="left" colspan="6">Сайт</td>
		</tr>
		<tr>
			<td align="left"><code>operator_sites</code></td>
			<td align="left">array</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Список уникальных идентификаторов и
адресов сайтов для которых доступен
оператор</td>
		</tr>
		<tr>
			<td align="left"><code>site_id</code></td>
			<td align="left">number</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Уникальный идентификатор сайта</td>
		</tr>
		<tr>
			<td align="left"><code>site_domain_name</code></td>
			<td align="left">string</td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left"></td>
			<td align="left">Адрес сайта в интернете. Без указания
протокола - <code>"http://"</code> или <code>"https://"</code>.</td>
		</tr>
	</tbody>
</table>

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.employees",
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
        "first_name":"string",
        "last_name":"string",
        "patronymic":"string",
        "full_name":"string",
        "email":"string",
        "groups":[
          {
            "group_id":"number",
            "group_name":"string"
          }
        ],
        "call_recording":"enum",
        "calls_available":"boolean",
        "schedule_id":"number",
        "schedule_name":"string",
        "coach":{
          "coach_id":"number",
          "coach_full_name":"string",
          "coach_always_enabled":"boolean"
        },
        "phone_numbers":[
          {
            "phone_number":"string",
            "channels_count":"number",
            "dial_time":"number",
            "status":"enum"
          }
        ],
        "extension":{
          "extension_phone_number":"string",
          "extension_voice_mail_enabled":"boolean",
          "extension_queue_enabled":"boolean"
        },
        "operator":{
          "operator_login":"string",
          "operator_position_id":"number",
          "operator_position_name":"string",
          "operator_offline_message_enabled":"boolean",
          "operator_invite_to_chat_enabled":"boolean",
          "operator_chat_enabled":"boolean",
          "operator_chats_available":"boolean",
          "operator_sites":[
            {
              "site_id":"number",
              "site_domain_name":"string"
            }
          ]
        }
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом get](#)"


## Создание сотрудника

Метод | `create.employees`
:---- | :---------------
Версия API | v2
Описание | Создание сотрудника
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
			<td>Уникальный идентификатор пользователя клиента агента от имени
которого делается запрос <blockquote>Является обязательным для агента</blockquote></td>
		</tr>
		<tr>
			<td><code>first_name</code></td>
			<td>string</td>
			<td>нет</td>
			<td></td>
			<td>Имя сотрудника</td>
		</tr>
		<tr>
			<td><code>last_name</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Фамилия сотрудника</td>
		</tr>
		<tr>
			<td><code>patronymic</code></td>
			<td>string</td>
			<td>нет</td>
			<td></td>
			<td>Отчество сотрудника</td>
		</tr>
		<tr>
			<td><code>email</code></td>
			<td>string</td>
			<td>нет</td>
			<td></td>
			<td>Адрес электронной почты сотрудника</td>
		</tr>
		<tr>
			<td><code>call_recording</code></td>
			<td>enum</td>
			<td>нет</td>
			<td>
				<ul>
					<li><code>all</code> - для
				всех
				звонков;</li>
					<li><code>in</code> - только
				для
				входящих;</li>
					<li><code>out</code> -
				только для
				исходящих;</li>
					<li><code>off</code> -
				отключена</li>
				</ul>
			</td>
			<td>Значение по умолчанию <code>"all"</code>. Статус записи разговоров <blockquote>Зависит от компонента "recording"</blockquote></td>
		</tr>
		<tr>
			<td><code>schedule_id</code></td>
			<td>number</td>
			<td>нет</td>
			<td></td>
			<td>График активности</td>
		</tr>
		<tr>
			<td><code>calls_available</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>Значение по умолчанию <code>"true"</code>. Доступность для звонков</td>
		</tr>
		<tr>
			<td colspan="5">Тренер</td>
		</tr>
		<tr>
			<td><code>coach</code></td>
			<td>object</td>
			<td>нет</td>
			<td></td>
			<td>Тренер для сотрудника <blockquote>Зависит от компонента <code>"trainer"</code></blockquote></td>
		</tr>
		<tr>
			<td><code>coach_always_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>
				По умолчанию <code>"false"</code>. При активации опции все входящие звонки
				сотрудника будут дублироваться его тренеру.
				<blockquote>Значение <code>"true"</code> возможно установить если задан
параметр <code>"coach_id"</code>.</blockquote>
			</td>
		</tr>
		<tr>
			<td><code>coach_id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор тренера</td>
		</tr>
		<tr>
			<td colspan="5">Группы в которых состоит сотрудник</td>
		</tr>
		<tr>
			<td><code>groups</code></td>
			<td>array</td>
			<td>нет</td>
			<td></td>
			<td>Список уникальных идентификаторов групп в которых состоит
сотрудник.</td>
		</tr>
		<tr>
			<td colspan="5">Телефоны</td>
		</tr>
		<tr>
			<td><code>phone_numbers</code></td>
			<td>array</td>
			<td>да</td>
			<td>10 штук</td>
			<td>Список телефонов сотрудника <blockquote>Важно понимать, что при создании нового сотрудника
номер уже может существовать у другого сотрудника и
если номеру переданы новые параметры, то они будут
так же обновлены уже существующему номеру</blockquote></td>
		</tr>
		<tr>
			<td><code>phone_number</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>
				Номер телефона сотрудника. Формат номера может быть с
				донабором, к примеру "74955140578...2345", поэтому у номера не
				формат E164
				<blockquote>Если указан SIP, то не делаем связки, а просто добавляем
как номер типа ТФОП, т.е. как обычный номер</blockquote>
			</td>
		</tr>
		<tr>
			<td><code>channels_count</code></td>
			<td>number</td>
			<td>нет</td>
			<td>От 1 до 30</td>
			<td>Значение по умолчанию <code>"1"</code>. Количество линий на телефоне.</td>
		</tr>
		<tr>
			<td><code>dial_time</code></td>
			<td>number</td>
			<td>нет</td>
			<td>От 1 до 100</td>
			<td>Значение по умолчанию <code>"60"</code>. Время дозвона по телефону.
Значение в секундах.</td>
		</tr>
		<tr>
			<td><code>status</code></td>
			<td>enum</td>
			<td>нет</td>
			<td><code>active</code>, <code>inactive</code></td>
			<td>Значение по умолчанию <code>"active"</code>. Статус номера.</td>
		</tr>
		<tr>
			<td colspan="5">Внутренний номер</td>
		</tr>
		<tr>
			<td><code>extension</code></td>
			<td>object</td>
			<td>нет</td>
			<td></td>
			<td>Внутренний номер сотрудника</td>
		</tr>
		<tr>
			<td><code>extension_phone_number</code></td>
			<td>number</td>
			<td>да</td>
			<td>Максимальная
длина 4</td>
			<td>Внутренний номер</td>
		</tr>
		<tr>
			<td><code>extension_voice_mail_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>
				Значение по умолчанию <code>"false"</code>.<br>
				В случае, если все номера, указанные для этого сотрудника в
				списке телефонов, заняты, то звонящему абоненту будет
				предложено оставить голосовое сообщение.
			</td>
		</tr>
		<tr>
			<td><code>extension_queue_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>
				Значение по умолчанию <code>"false"</code>.<br>
				В случае, если все номера, указанные для этого сотрудника в
				списке телефонов, заняты, то звонящий абонент встанет в очередь
				на повторный дозвон до телефонов в списке и будет ждать первый
				освободившийся номер.
			</td>
		</tr>
		<tr>
			<td colspan="5">Является ли сотрудник чатом</td>
		</tr>
		<tr>
			<td><code>operator</code></td>
			<td>object</td>
			<td>нет</td>
			<td></td>
			<td>Оператор рабочего места <blockquote>Зависит от компонента <code>"consultant"</code></blockquote></td>
		</tr>
		<tr>
			<td><code>operator_login</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Логин сотрудника для входа в приложение «Рабочее место
оператора»</td>
		</tr>
		<tr>
			<td><code>operator_password</code></td>
			<td>string</td>
			<td>да</td>
			<td>Минимальная
длина 8</td>
			<td>Пароль сотрудника для входа в приложение «Рабочее место
оператора»</td>
		</tr>
		<tr>
			<td><code>operator_position_id</code></td>
			<td>number</td>
			<td>нет</td>
			<td></td>
			<td>Должность сотрудника в подписи</td>
		</tr>
		<tr>
			<td><code>operator_offline_message_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>Значение по умолчанию <code>"false"</code>. Разрешено ли обрабатывать заявки</td>
		</tr>
		<tr>
			<td><code>operator_invite_to_chat_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>Значение по умолчанию <code>"false"</code>. Разрешено ли приглашать в чат</td>
		</tr>
		<tr>
			<td><code>operator_chat_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>Значение по умолчанию <code>"true"</code>. Разрешено ли участвовать в чатах с
посетителями</td>
		</tr>
		<tr>
			<td><code>operator_sites</code></td>
			<td>array</td>
			<td>нет</td>
			<td></td>
			<td>Список уникальных идентификаторов сайтов для которых доступен
сотрудник.</td>
		</tr>
	</tbody>
</table>

### Параметры ответа

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`id` | number | да |  | Уникальный идентификатор сотрудника

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"create.employees",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "first_name":"string",
    "last_name":"string",
    "patronymic":"string",
    "email":"string",
    "groups":[
      "group_id"
    ],
    "call_recording":"enum",
    "calls_available":"boolean",
    "schedule_id":"number",
    "coach":{
      "coach_always_enabled":"boolean",
      "coach_id":"number"
    },
    "phone_numbers":[
      {
        "phone_number":"number",
        "channels_count":"number",
        "dial_time":"number",
        "status":"enum"
      }
    ],
    "extension":{
      "extension_phone_number":"number",
      "extension_voice_mail_enabled":"boolean",
      "extension_queue_enabled":"boolean"
    },
    "operator":{
      "operator_login":"string",
      "operator_password":"string",
      "operator_position_id":"number",
      "operator_offline_message_enabled":"boolean",
      "operator_invite_to_chat_enabled":"boolean",
      "operator_chat_enabled":"boolean",
      "operator_sites":[
        "site_id"
      ]
    }
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


## Удаление сотрудника

Метод | `delete.employees`
:---- | :---------------
Версия API | v2
Описание | Удаление сотрудника
Кому доступен | Партнёр, Клиента
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`id` | number | да |  | Уникальный идентификатор сотрудника
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"delete.employees",
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


## Редактирование сотрудника

Метод | `update.employees`
:---- | :---------------
Версия API | v2
Описание | Создание сотрудника
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

> Возможно частичное обновление. Если обновляется массив данных, то переданный массив будет полностью заменять существующий.

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
			<td><code>id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор сотрудника</td>
		</tr>
		<tr>
			<td><code>user_id</code></td>
			<td>number</td>
			<td>нет</td>
			<td></td>
			<td>
				Уникальный идентификатор пользователя клиента агента от имени
				которого делается запрос
				<blockquote>Является обязательным для агента</blockquote>
			</td>
		</tr>
		<tr>
			<td><code>first_name</code></td>
			<td>string</td>
			<td>нет</td>
			<td></td>
			<td>Имя сотрудника</td>
		</tr>
		<tr>
			<td><code>last_name</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Фамилия сотрудника</td>
		</tr>
		<tr>
			<td><code>patronymic</code></td>
			<td>string</td>
			<td>нет</td>
			<td></td>
			<td>Отчество сотрудника</td>
		</tr>
		<tr>
			<td><code>email</code></td>
			<td>string</td>
			<td>нет</td>
			<td></td>
			<td>Адрес электронной почты сотрудника</td>
		</tr>
		<tr>
			<td><code>call_recording</code></td>
			<td>enum</td>
			<td>нет</td>
			<td>
				<ul>
					<li><code>all</code> - для всех звонков;</li>
					<li><code>in</code> - только для входящих;</li>
					<li><code>out</code> - только для исходящих;</li>
					<li><code>off</code> - отключена</li>
				</ul>
			</td>
			<td>
				Статус записи разговоров <blockquote>Зависит от компонента <code>"recording"</code></blockquote>
			</td>
		</tr>
		<tr>
			<td><code>schedule_id</code></td>
			<td>number</td>
			<td>нет</td>
			<td></td>
			<td>График активности</td>
		</tr>
		<tr>
			<td><code>calls_available</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>Доступность для звонков</td>
		</tr>
		<tr>
			<td colspan="5">Тренер</td>
		</tr>
		<tr>
			<td><code>coach</code></td>
			<td>object</td>
			<td>нет</td>
			<td></td>
			<td>
				Тренер для сотрудника
				<blockquote>Зависит от компонента <code>"trainer"</code></blockquote>
			</td>
		</tr>
		<tr>
			<td><code>coach_always_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>
				При активации опции все входящие звонки сотрудника будут
				дублироваться его тренеру.
				<blockquote>
					Значение <code>"true"</code> возможно установить если задан
					параметр <code>"coach_id"</code>.
				</blockquote>
			</td>
		</tr>
		<tr>
			<td><code>coach_id</code></td>
			<td>number</td>
			<td>нет</td>
			<td></td>
			<td>Уникальный идентификатор тренера</td>
		</tr>
		<tr>
			<td colspan="5">Группы в которых состоит сотрудник</td>
		</tr>
		<tr>
			<td><code>groups</code></td>
			<td>array</td>
			<td>нет</td>
			<td></td>
			<td>Список уникальных идентификаторов групп в которых состоит
сотрудник</td>
		</tr>
		<tr>
			<td colspan="5">Телефоны</td>
		</tr>
		<tr>
			<td><code>phone_numbers</code></td>
			<td>array</td>
			<td>да</td>
			<td>10 штук</td>
			<td>Список телефонов сотрудника
			<blockquote>
				Важно понимать, что при создании нового сотрудника
				номер уже может существовать у другого сотрудника и
				если номеру переданы новые параметры, то они будут
				так же обновлены уже существующему номеру
			</blockquote></td>
		</tr>
		<tr>
			<td><code>phone_number</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Номер телефона сотрудника</td>
		</tr>
		<tr>
			<td><code>channels_count</code></td>
			<td>number</td>
			<td>нет</td>
			<td>От 1 до 30</td>
			<td>Количество линий на телефоне</td>
		</tr>
		<tr>
			<td><code>dial_time</code></td>
			<td>number</td>
			<td>нет</td>
			<td>От 1 до 100</td>
			<td>Время дозвона по телефону</td>
		</tr>
		<tr>
			<td><code>status</code></td>
			<td>enum</td>
			<td>нет</td>
			<td><code>active</code>, <code>inactive</code></td>
			<td>Статус номера.</td>
		</tr>
		<tr>
			<td colspan="5">Внутренний номер</td>
		</tr>
		<tr>
			<td><code>extension</code></td>
			<td>object</td>
			<td>нет</td>
			<td></td>
			<td>Внутренний номер сотрудника</td>
		</tr>
		<tr>
			<td><code>extension_phone_number</code></td>
			<td>number</td>
			<td>да</td>
			<td>Максимальная длина 4</td>
			<td>Внутренний номер</td>
		</tr>
		<tr>
			<td><code>extension_voice_mail_enabled</code></td>
			<td>boolean</td>
			<td>да</td>
			<td><code>true</code>, <code>false</code></td>
			<td>В случае, если все номера, указанные для этого сотрудника в
списке телефонов, заняты, то звонящему абоненту будет
предложено оставить голосовое сообщение.</td>
		</tr>
		<tr>
			<td><code>extension_queue_enabled</code></td>
			<td>boolean</td>
			<td>да</td>
			<td><code>true</code>, <code>false</code></td>
			<td>В случае, если все номера, указанные для этого сотрудника в
списке телефонов, заняты, то звонящий абонент встанет в очередь
на повторный дозвон до телефонов в списке и будет ждать первый
освободившийся номер.</td>
		</tr>
		<tr>
			<td colspan="5">Является ли сотрудник чатом</td>
		</tr>
		<tr>
			<td><code>operator</code></td>
			<td>object</td>
			<td>нет</td>
			<td></td>
			<td>Оператор рабочего места <blockquote>Зависит от компонента <code>"consultant"</code></blockquote></td>
		</tr>
		<tr>
			<td><code>operator_login</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Логин сотрудника для входа в приложение «Рабочее место
оператора»</td>
		</tr>
		<tr>
			<td><code>operator_password</code></td>
			<td>string</td>
			<td>да</td>
			<td>Минимальная
длина 8</td>
			<td>Пароль сотрудника для входа в приложение «Рабочее место
оператора»</td>
		</tr>
		<tr>
			<td><code>operator_position_id</code></td>
			<td>number</td>
			<td>нет</td>
			<td></td>
			<td>Должность сотрудника в подписи</td>
		</tr>
		<tr>
			<td><code>operator_offline_message_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>Разрешено ли обрабатывать заявки</td>
		</tr>
		<tr>
			<td><code>operator_invite_to_chat_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>Разрешено ли приглашать в чат</td>
		</tr>
		<tr>
			<td><code>operator_chat_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td><code>true</code>, <code>false</code></td>
			<td>Разрешено ли участвовать в чатах с посетителями</td>
		</tr>
		<tr>
			<td><code>operator_sites</code></td>
			<td>array</td>
			<td>нет</td>
			<td></td>
			<td>Список уникальных идентификаторов сайтов для которых доступен
сотрудник.</td>
		</tr>
	</tbody>
</table>

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"update.employees",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "first_name":"string",
    "last_name":"string",
    "patronymic":"string",
    "email":"string",
    "groups":[
      "group_id"
    ],
    "call_recording":"enum",
    "calls_available":"boolean",
    "schedule_id":"number",
    "coach":{
      "coach_always_enabled":"boolean",
      "coach_id":"number"
    },
    "phone_numbers":[
      {
        "phone_number":"number",
        "channels_count":"number",
        "dial_time":"number",
        "status":"enum"
      }
    ],
    "extension":{
      "extension_phone_number":"number",
      "extension_voice_mail_enabled":"boolean",
      "extension_queue_enabled":"boolean"
    },
    "operator":{
      "operator_login":"string",
      "operator_password":"string",
      "operator_position_id":"number",
      "operator_offline_message_enabled":"boolean",
      "operator_invite_to_chat_enabled":"boolean",
      "operator_chat_enabled":"boolean",
      "operator_sites":[
        "site_id"
      ]
    }
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


## Создание группы сотрудников

Метод | `create.group_employees`
:---- | :---------------
Версия API | v2
Описание | Создание группы сотрудников
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
				Уникальный идентификатор пользователя клиента агента от имени
				которого делается запрос <blockquote>Является обязательным для агента</blockquote>
			</td>
		</tr>
		<tr>
			<td><code>name</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Название группы</td>
		</tr>
		<tr>
			<td colspan="5">Список сотрудников в группе</td>
		</tr>
		<tr>
			<td><code>members</code></td>
			<td>array</td>
			<td>нет</td>
			<td></td>
			<td>Список уникальных идентификаторов сотрудников, которые состоят в
группе</td>
		</tr>
		<tr>
			<td colspan="5">Настройка внутреннего номера группы</td>
		</tr>
		<tr>
			<td><code>group_phone_number</code></td>
			<td>number</td>
			<td>нет</td>
			<td>Максимальная
длина 4</td>
			<td>Внутренний номер группы <blockquote>Зависит от компонента <code>"va"</code></blockquote></td>
		</tr>
		<tr>
			<td><code>queue_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td></td>
			<td>
				Значение по умолчанию <code>"false"</code>. В случае, если все номера, указанные
				для этой группы сотрудников, заняты, то звонящий абонент встанет в
				очередь на повторный дозвон до телефонов в списке и будет ждать
				первый освободившийся номер.
				<blockquote>Зависит от компонента <code>"va"</code></blockquote>
			</td>
		</tr>
		<tr>
			<td><code>channels_count</code></td>
			<td>number</td>
			<td>нет</td>
			<td>От 1 до 199</td>
			<td>
				Значение по умолчанию <code>1</code>.<br>
				Количество одновременных линий при обзвоне
				<blockquote>Зависит от компонента <code>"va"</code></blockquote>
			</td>
		</tr>
	</tbody>
</table>

### Параметры ответа

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`id` | number | да |  | Уникальный идентификатор группы

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"create.group_employees",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "name":"string",
    "members":[
      "employee_id"
    ],
    "group_phone_number":"number",
    "queue_enabled":"boolean",
    "channels_count":"number"
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


## Удаление группы сотрудников

Метод | `delete.group_employees`
:---- | :---------------
Версия API | v2
Описание | Удаление группы сотрудников
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`id` | number | да |  | Уникальный идентификатор группы
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"delete.group_employees",
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


## Редактирование группы сотрудников

Метод | `update.group_employees`
:---- | :---------------
Версия API | v2
Описание | Удаление группы сотрудников
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

> Возможно частичное обновление. Если обновляется массив данных, то переданный массив будет полностью заменять существующий.

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
			<td><code>id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор группы</td>
		</tr>
		<tr>
			<td><code>user_id</code></td>
			<td>number</td>
			<td>нет</td>
			<td></td>
			<td>
				Уникальный идентификатор пользователя клиента агента от имени
				которого делается запрос
				<blockquote>Является обязательным для агента</blockquote>
			</td>
		</tr>
		<tr>
			<td><code>name</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Название группы</td>
		</tr>
		<tr>
			<td colspan="5">Список сотрудников в группе</td>
		</tr>
		<tr>
			<td><code>members</code></td>
			<td>array</td>
			<td>нет</td>
			<td></td>
			<td>
				Список уникальных идентификаторов сотрудников, которые состоят в
				группе
			</td>
		</tr>
		<tr>
			<td colspan="5">Настройки внутреннего номера группы</td>
		</tr>
		<tr>
			<td><code>group_phone_number</code></td>
			<td>number</td>
			<td>нет</td>
			<td>Максимальная
длина 4</td>
			<td>Внутренний номер группы <blockquote>Зависит от компонента <code>"va"</code></blockquote></td>
		</tr>
		<tr>
			<td><code>queue_enabled</code></td>
			<td>boolean</td>
			<td>нет</td>
			<td></td>
			<td>
				Значение по умолчанию <code>"false"</code>. В случае, если все номера, указанные
				для этой группы сотрудников, заняты, то звонящий абонент встанет в
				очередь на повторный дозвон до телефонов в списке и будет ждать
				первый освободившийся номер. <blockquote>Зависит от компонента <code>"va"</code></blockquote>
			</td>
		</tr>
		<tr>
			<td><code>channels_count</code></td>
			<td>number</td>
			<td>да</td>
			<td>От 1 до 199</td>
			<td>Количество одновременных линий при обзвоне <blockquote>Зависит от компонента <code>"va"</code></blockquote></td>
		</tr>
	</tbody>
</table>

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"update.group_employees",
  "params":{
    "access_token":"string",
    "id":"number",
    "user_id":"number",
    "name":"string",
    "members":[
      "employe_id"
    ],
    "group_phone_number":"number",
    "queue_enabled":"boolean",
    "channels_count":"number"
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


## Получение списка групп сотрудников

Метод | `get.group_employees`
:---- | :---------------
Версия API | v2
Описание | Получение списка групп сотрудников
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать <code>"limit"</code> записей. По умолчанию <code>"0"</code>.
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
			<td>Уникальный идентификатор группы</td>
		</tr>
		<tr>
			<td><code>name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>Название группы</td>
		</tr>
		<tr>
			<td colspan="6">Список сотрудников в группе</td>
		</tr>
		<tr>
			<td><code>members</code></td>
			<td>array</td>
			<td></td>
			<td></td>
			<td></td>
			<td>
				Список уникальных идентификаторов сотрудников,
				которые состоят в группе
			</td>
		</tr>
		<tr>
			<td><code>employee_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор сотрудника</td>
		</tr>
		<tr>
			<td><code>employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Ф.И.О. сотрудника</td>
		</tr>
		<tr>
			<td colspan="6">Список номеров сотрудников в группе и их доступность</td>
		</tr>
		<tr>
			<td><code>phone_numbers</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>
				Список городских, мобильных и sip номеров
				сотрудников, которые входят в группу, с указанием
				их доступности и приоритетом обзвона. Приоритет
				обзвона номеров определяется положением номера в
				списке. Обзвон указанного списка номеров в группе
				возможен по внутреннему номеру группы (см.
				параметр <code>"group_phone_number"</code>). Для изменения
				приоритета и доступности номера в группе см. метод
				<code>"update.group_employees_numbers"</code>
			</td>
		</tr>
		<tr>
			<td><code>employee_phone_number</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Номер телефона сотрудника</td>
		</tr>
		<tr>
			<td><code>employee_phone_number_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор номера сотрудника в
группе</td>
		</tr>
		<tr>
			<td><code>employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Ф.И.О. сотрудника</td>
		</tr>
		<tr>
			<td><code>employee_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор сотрудника</td>
		</tr>
		<tr>
			<td><code>available</code></td>
			<td>boolean</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Доступность номера в группе</td>
		</tr>
		<tr>
			<td colspan="6">Настройка внутреннего номмера группы</td>
		</tr>
		<tr>
			<td><code>group_phone_number</code></td>
			<td>number</td>
			<td>Максимальная
длина 4</td>
			<td>да</td>
			<td>да</td>
			<td>Внутренний номер группы</td>
		</tr>
		<tr>
			<td><code>queue_enabled</code></td>
			<td>boolean</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>
				Значение по умолчанию <code>"false"</code>. В случае, если все
				номера, указанные для этой группы сотрудников,
				заняты, то звонящий абонент встанет в очередь на
				повторный дозвон до телефонов в списке и будет
				ждать первый освободившийся номер.
			</td>
		</tr>
		<tr>
			<td><code>channels_count</code></td>
			<td>number</td>
			<td>От 1 до 199</td>
			<td>да</td>
			<td></td>
			<td>Количество одновременных линий при обзвоне</td>
		</tr>
	</tbody>
</table>

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.group_employees",
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
        "members":[
          {
            "employee_id":"number",
            "employee_full_name":"string"
          }
        ],
        "phone_number":[
          {
            "employee_phone_number":"number",
            "employee_phone_number_id":"number",
            "employee_full_name":"string",
            "employee_id":"number",
            "available":"boolean"
          }
        ],
        "group_phone_number":"number",
        "queue_enabled":"boolean",
        "channels_count":"number"
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом get](#)"


## Изменение приоритета и доступности номера сотрудника в группе сотрудников

Метод | `update.group_employees_numbers`
:---- | :---------------
Версия API | v2
Описание | Изменение приоритета и доступности номера сотрудника в группе сотрудников
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

> Если номер не передан в списке номеров, то и данные по номеру не обновляются.

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
			<td><code>id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор группы</td>
		</tr>
		<tr>
			<td><code>user_id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>
				Уникальный идентификатор пользователя клиента агента от имени
				которого делается запрос
				<blockquote>Является обязательным для агента</blockquote>
			</td>
		</tr>
		<tr>
			<td colspan="5">Список номеров сотрудников в группе и их доступность</td>
		</tr>
		<tr>
			<td><code>phone_numbers</code></td>
			<td>array</td>
			<td>да</td>
			<td></td>
			<td>
				Список городских, мобильных и sip номеров сотрудников, которые
				входят в группу, с указанием их доступности и приоритетом
				обзвона. Приоритет обзвона номеров определяется положением
				номера в списке. Обзвон указанного списка номеров в группе
				возможен по внутреннему номеру группы (см. параметр
				<code>"group_phone_number"</code>).
				<blockquote>Нужно передавать все номера или будет ошибка
<code>"invalid_aparameter_value"</code></blockquote>
			</td>
		</tr>
		<tr>
			<td><code>employee_phone_number_id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор номера сотрудника в группе</td>
		</tr>
		<tr>
			<td><code>available</code></td>
			<td>boolean</td>
			<td>да</td>
			<td></td>
			<td>Доступность номера в группе</td>
		</tr>
	</tbody>
</table>

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"update.group_employees_numbers",
  "params":{
    "access_token":"string",
    "id":"number",
    "user_id":"number",
    "phone_numbers":[
      {
        "employe_phone_number_id":"number",
        "available":"boolean"
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

  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом update](#)"

\+

Текст ошибки | Мнемоника | Код | Описание
:----------- | :-------- | :-- | :-------
*Invalid parameter value* | `invalid_parameter_value` | -32602 | Если переданы не все номера в массиве phone_numbers


## Получение списка должностей сотрудников

Метод | `get.employee_positions`
:---- | :---------------
Версия API | v2
Описание | Получение списка должностей сотрудников
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать <code>"limit"</code> записей. По умолчанию <code>"0"</code>.
`filter` | object | нет |  | См. раздел **"Критерии фильтрации"**
`fields` | array | нет |  | См. раздел **"Представление возвращаемых данных"**
`sort` | array | нет |  | См. раздел **"Сортировка данных"**

### Параметры ответа

Название | Тип  | Допустимые значения | Фильтрация | Сортировка | Описание
:------- | :--- | :-----------------: | :--------- | :--------- | :-------
`id` | number |  | да |  | Уникальный идентификатор должности сотрудника
`name` | string |  | да | да | Название должности сотрудника

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.employee_positions",
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
        "name":"string"
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом get](#)"


## Добавление должности сотрудника

Метод | `create.employee_positions`
:---- | :---------------
Версия API | v2
Описание | Добавление должности сотрудника
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`name` | string | да |  | Название должности

### Параметры ответа

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`id` | number | да |  | Уникальный идентификатор должности

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"create.employee_positions",
  "params":{
    "access_token":"string",
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
    "id":"number"
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "[Список ошибок для методов с глаголом create](#)"


## Редактирование должности сотрудника

Метод | `update.employee_positions`
:---- | :---------------
Версия API | v2
Описание | Редактирование должности сотрудника
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`name` | string | да |  | Название должности
`id` | number | да |  | Уникальный идентификатор должности

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"update.employee_positions",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "id":"number",
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


## Удаление должности сотрудника

Метод | `delete.employee_positions`
:---- | :---------------
Версия API | v2
Описание | Удаление должности сотрудника
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`id` | number | да |  | Уникальный идентификатор должности сотрудника
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"delete.employee_positions",
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