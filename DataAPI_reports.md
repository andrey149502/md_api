# Управление отчётами

**ЧАСТИЧНО ДОСТУПНО КЛИЕНТАМ**

> По умолчанию максимальный период выгрузки отчёта с даты получения запроса = 3 месяца. Возвращаемая ошибка `date_interval_limit_reached`

## `ДОСТУПНО КЛИЕНТАМ` Получение списка всех обращений

Метод | `get.communications_report`
:---- | :---------------
Версия API | v2
Описание | Получение списка всех обращений
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"
`date_from` | iso8601 | да |  | Дата начала выборки
`date_till` | iso8601 | да |  | Дата окончания выборки

### Параметры ответа

<table>
	<tbody>
		<tr>
			<th>Название</th>
			<th>Тип</th>
			<th>Допустимые значения</th>
			<th>Фильтрация</th>
			<th>Сортировка</th>
			<th>Ответ по умолчанию</th>
			<th>Описание</th>
		</tr>
		<tr>
			<td><code>id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>
				Уникальный
				идентификатор
				обращения. Для
				получения
				детализированной
				информации по каждому
				типу обращения можно
				использовать следующие
				методы: <code>"get.chats_report"</code>,
				<code>"get.goals_report"</code>, <code>"get.offline_messages_report"</code>, <code>"get.calls_report"</code>
			</td>
		</tr>
		<tr>
			<td><code>communication_type</code></td>
			<td>enum</td>
			<td>
				<code>chat</code>, <code>call</code>, <code>goal</code>,
				<code>offline_message</code>
			</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>
				Тип обращения. Для
				получения
				детализированной
				информации по каждому
				типу обращения можно
				использовать следующие
				методы: <code>"get.chats_report"</code>,
				<code>"get.goals_report"</code>, <code>"get.offline_messages_report"</code>, <code>"get.calls_report"</code>
			</td>
		</tr>
		<tr>
			<td><code>communication_number</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>
				Номер обращения.
				Расcчитывается в рамках
				персоны.
			</td>
		</tr>
		<tr>
			<td><code>date_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Дата и время обращения</td>
		</tr>
		<tr>
			<td><code>ua_client_id</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный
идентификатор в Universal
Analytics</td>
		</tr>
		<tr>
			<td><code>sale_date</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Дата сделки</td>
		</tr>
		<tr>
			<td><code>sale_cost</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Сумма сделки</td>
		</tr>
		<tr>
			<td><code>search_query</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Поисковый запрос</td>
		</tr>
		<tr>
			<td><code>search_engine</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название поисковой
системы</td>
		</tr>
		<tr>
			<td><code>referrer_domain</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Домен реферера</td>
		</tr>
		<tr>
			<td><code>referrer</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Источник перехода</td>
		</tr>
		<tr>
			<td><code>entrance_page</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Страница входа</td>
		</tr>
		<tr>
			<td><code>gclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Google Click Identifier</td>
		</tr>
		<tr>
			<td><code>yclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Yandex Click Identifier</td>
		</tr>
		<tr>
			<td><code>ymclid</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Yandex Market Click
Identifier</td>
		</tr>
		<tr>
			<td><code>ef_id</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Используется для
разметки ссылок в
системе управления
контекстной рекламой
AdLense</td>
		</tr>
		<tr>
			<td><code>channel</code></td>
			<td>enum</td>
			<td>
			<ul>
				<li><code>advert</code></li>
				<li><code>organic</code></li>
				<li><code>referral</code></li>
				<li><code>direct</code></li>
				<li><code>paid</code></li>
				<li><code>display</code></li>
				<li><code>affiliate</code></li>
				<li><code>email</code></li>
				<li><code>social</code></li>
				<li><code>internal</code></li>
			</ul>
			</td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Канал.</td>
		</tr>
		<tr>
			<td colspan="7">Проставленные теги</td>
		</tr>
		<tr>
			<td><code>tags</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Теги, см. метод <code>"get.tags"</code></td>
		</tr>
		<tr>
			<td><code>tag_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный
идентификатор тега</td>
		</tr>
		<tr>
			<td><code>tag_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название тега</td>
		</tr>
		<tr>
			<td><code>tag_type</code></td>
			<td>enum</td>
			<td><code>auto</code>, <code>manual</code></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Тип тега</td>
		</tr>
		<tr>
			<td><code>tag_change_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Дата и время простановки
тега</td>
		</tr>
		<tr>
			<td><code>tag_user_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный
идентификатор
пользователя, который
проставил тег</td>
		</tr>
		<tr>
			<td><code>tag_user_login</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Логин пользователя,
который проставил тег</td>
		</tr>
		<tr>
			<td><code>tag_employee_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный
идентификатор
сотрудника, который
проставил тег</td>
		</tr>
		<tr>
			<td><code>tag_employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Ф.И.О. сотрудника
который проставил тег</td>
		</tr>
		<tr>
			<td colspan="7">Информация о посетителе</td>
		</tr>
		<tr>
			<td><code>visitor_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный
идентификатор
посетителя</td>
		</tr>
		<tr>
			<td><code>person_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный
идентификатор персоны</td>
		</tr>
		<tr>
			<td><code>visitor_type</code></td>
			<td>enum</td>
			<td>Новый, Вернувшийся, Не
заполнен</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Тип посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_session_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный идентификатор сессии посетителя, см. <code>"get.visitor_session_report"</code></td>
		</tr>
		<tr>
			<td><code>visits_count</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Количество посещений</td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор первой рекламной кампании. См. метод <code>"get.campaigns"</code></td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название первой рекламной кампании</td>
		</tr>
		<tr>
			<td><code>visitor_city</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Город посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_region</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Регион посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_country</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Страна посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_device</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>desktop</code></li>
					<li><code>mobile</code></li>
					<li><code>tablet</code></li>
					<li><code>other</code></li>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Устройство посетителя</td>
		</tr>
		<tr>
			<td colspan="7">Свойства посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_custom_properties</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Свойства посетителя,
				которые могут быть
				заданы через личный
				кабинет или с помощью JavaScript API [метод <code>Comagic.setProperty(name, value);</code>]
			</td>
		</tr>
		<tr>
			<td><code>property_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>
				Имя свойства, которое
				должно быть присвоено
				посетителю
			</td>
		</tr>
		<tr>
			<td><code>property_value</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Значение свойства</td>
		</tr>
		<tr>
			<td colspan="7">Сайт</td>
		</tr>
		<tr>
			<td><code>site_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный
идентификатор сайта</td>
		</tr>
		<tr>
			<td><code>site_domain_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Адрес сайта в интернете.
				Без указания протокола -
				<code>"http://"</code> или <code>"https://"</code>
			</td>
		</tr>
		<tr>
			<td colspan="7">Рекламная кампания</td>
		</tr>
		<tr>
			<td><code>campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный
идентификатор рекламной
кампании</td>
		</tr>
		<tr>
			<td><code>campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название рекламной
кампании</td>
		</tr>
		<tr>
			<td><code>visit_other_campaign</code></td>
			<td>boolean</td>
			<td><code>true</code>, <code>false</code></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Флаг показывает заходил
ли посетитель (в пределах
персоны) по другим
рекламным кампаниям</td>
		</tr>
		<tr>
			<td colspan="7">Сегменты</td>
		</tr>
		<tr>
			<td><code>segments</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Сегменты, см. метод <code>"get.segments"</code>
			</td>
		</tr>
		<tr>
			<td><code>segment_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название сегмента</td>
		</tr>
		<tr>
			<td><code>segment_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный
идентификатор сегмента</td>
		</tr>
		<tr>
			<td colspan="7">UTM-метки</td>
		</tr>
		<tr>
			<td><code>utm_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Источник кампании</td>
		</tr>
		<tr>
			<td><code>utm_medium</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Канал кампании</td>
		</tr>
		<tr>
			<td><code>utm_term</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Ключевое слово
кампании</td>
		</tr>
		<tr>
			<td><code>utm_content</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Содержание кампании</td>
		</tr>
		<tr>
			<td><code>utm_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название кампании</td>
		</tr>
		<tr>
			<td colspan="7">OS-метки</td>
		</tr>
		<tr>
			<td><code>openstat_ad</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор
рекламного объявления</td>
		</tr>
		<tr>
			<td><code>openstat_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор рекламной
кампании</td>
		</tr>
		<tr>
			<td><code>openstat_service</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор сервиса,
предоставляющего услуги</td>
		</tr>
		<tr>
			<td><code>openstat_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор площадки,
раздела, страницы, места
на странице, на котором
было показано
соответствующее
рекламное объявление</td>
		</tr>
		<tr>
			<td colspan="7">Атрибуты обращения</td>
		</tr>
		<tr>
			<td><code>attributes</code></td>
			<td>array</td>
			<td>
				<ul>
					<li><code>primary</code> - Первичное</li>
					<li><code>secondary</code> - Вторичное</li>
					<li><code>lost</code> - Потерянное</li>
					<li><code>target</code> - Целевое</li>
					<li><code>off-target</code> - Не целевое</li>
					<li><code>quality</code> - Качественное</li>
					<li><code>rest</code> - целевые повторные обращения (обращения, совершенные в период повторного обращения, настроенного для сайта в ЛК CoMagic).</li>
				</ul>
			</td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Атрибут обращения</td>
		</tr>
	</tbody>
</table>


### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.communications_report",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "offset":"number",
    "limit":"number",
    "date_from":"iso8601",
    "date_till":"iso8601",
    "filter":{

    },
    "sort":[
      {
        "field":"string",
        "order":"string"
      }
    ],
    "field":[
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
        "communication_type":"enum",
        "communication_number":"number",
        "date_time":"iso8601",
        "ua_client_id":"string",
        "sale_date":"iso8601",
        "sale_cost":"number",
        "search_query":"string",
        "search_engine":"string",
        "referrer_domain":"string",
        "referrer":"string",
        "entrance_page":"string",
        "gclid":"string",
        "yclid":"string",
        "ymclid":"string",
        "ef_id":"string",
        "channel":"enum",
        "tags":[
          {
            "tag_id":"number",
            "tag_name":"string",
            "tag_type":"enum",
            "tag_change_time":"iso8601",
            "tag_user_id":"number",
            "tag_user_login":"string",
            "tag_employee_id":"number",
            "tag_employee_full":"string"
          }
        ],
        "site_id":"number",
        "site_domain_name":"string",
        "campaign_id":"number",
        "campaign_name":"string",
        "visit_other_campaign":"boolean",
        "visitor_id":"number",
        "person_id":"number",
        "visitor_type":"enum",
        "visitor_session_id":"number",
        "visits_count":"number",
        "visitor_first_campaign_id":"number",
        "visitor_first_campaign_name":"string",
        "visitor_city":"string",
        "visitor_region":"string",
        "visitor_country":"string",
        "visitor_device":"enum",
        "visitor_custom_properties":[
          {
            "property_name":"string",
            "property_value":"string"
          }
        ],
        "segments":[
          {
            "segment_id":"number",
            "segment_name":"string"
          }
        ],
        "utm_source":"string",
        "utm_medium":"string",
        "utm_term":"string",
        "utm_content":"string",
        "utm_campaign":"string",
        "openstat_ad":"string",
        "openstat_campaign":"string",
        "openstat_service":"string",
        "openstat_source":"string",
        "attributes":[

        ]
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "Список ошибок для методов с глаголом get"


## `ДОСТУПНО КЛИЕНТАМ` Получение отчёта по сессиям звонков

Метод | `get.calls_report`
:---- | :---------------
Версия API | v2
Описание | Получение отчёта по сессиям звонков "Список обращений" -> "Звонки"
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"
`date_from` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата начала выборки
`date_till` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата окончания выбокри

### Параметры ответа

<table>
	<tbody>
		<tr>
			<th>Название</th>
			<th>Тип</th>
			<th>Допустимые значения</th>
			<th>Фильтрация</th>
			<th>Сортировка</th>
			<th>Ответ по умолчанию</th>
			<th>Описание</th>
		</tr>
		<tr>
			<td><code>id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный идентификатор сессии звонка</td>
		</tr>
		<tr>
			<td><code>start_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>Дата и время начал сессии звонка</td>
		</tr>
		<tr>
			<td><code>finish_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>Время окончания сессии звонка</td>
		</tr>
		<tr>
			<td><code>finish_reason</code></td>
			<td>enum</td>
			<td>
				<code>incorrect_input</code>
				<code>numb_not_exists</code>
				<code>numb_is_inactive</code>
				<code>sitephone_is_not_configured</code>
				<code>app_is_inactive</code>
				<code>numa_in_black_list</code>
				<code>no_active_scenario</code>
				<code>simple_forwarding_is_not_configured</code>
				<code>site_not_exists</code>
				<code>call_generator_is_not_configured</code>
				<code>add_cdr_timeout</code>
				<code>success_finish</code>
				<code>api_permission_denied</code>
				<code>api_ip_now_allowed</code>
				<code>component_is_inactive</code>
				<code>employee_not_exists</code>
				<code>not_enough_money</code>
				<code>platform_not_found</code>
				<code>internal_error</code>
				<code>incorrect_config</code>
				<code>communication_unavailable</code>
			</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Причина окончания сессии звонка</td>
		</tr>
		<tr>
			<td><code>direction</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>in</code> - Входящая;</li>
					<li><code>out</code> - Исходящая</li>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Направление сессии звонка</td>
		</tr>
		<tr>
			<td><code>source</code></td>
			<td>enum</td>
			<td>
			<ul>
				<li><code>callapi</code> - Call API;</li>
				<li><code>callapi_informer_call</code> - Call API Информационный звонок</li>
				<li><code>callapi_scenario_call</code> - Call API вызов сценария</li>
				<li><code>callback</code> - Callback;</li>
				<li><code>callout</code> - Callout;</li>
				<li><code>call_tracking</code>- Аналитика;</li>
				<li><code>dynamic_call_tracking</code> - Динамический call tracking</li>
				<li><code>va</code> - Виртуальная АТС;</li>
				<li><code>sip</code> - Исходящий с SIP;</li>
				<li><code>consultant</code> - Звонок через Консультант;</li>
				<li><code>lead</code> - Звонок через Лидогенератор;</li>
				<li><code>sitephone</code> - Звонок через Сайтфон;</li>
				<li><code>retailcrm</code> - Звонок из retailCRM;</li>
				<li><code>faxout</code> - Исходящий факс</li>
			</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Источник звонка</td>
		</tr>
		<tr>
			<td><code>is_lost</code></td>
			<td>boolean</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Признак, что звонок потерянный или успешный</td>
		</tr>
		<tr>
			<td><code>communication_number</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Для сесии ВАТС пустой всегда, такова сейчас идеология сервиса</td>
		</tr>
		<tr>
			<td><code>communication_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный идентификатор обращения</td>
		</tr>
		<tr>
			<td><code>communication_type</code></td>
			<td>enum</td>
			<td><code>call</code></td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>Тип обращения</td>
		</tr>
		<tr>
			<td><code>wait_duration</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Длительность ожидания до первого разговора в секундах</td>
		</tr>
		<tr>
			<td><code>total_wait_duration</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Полная длительность ожидания звонящего на линии, значение в секундах</td>
		</tr>
		<tr>
			<td><code>talk_duration</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>	Длительность разговора. Считается от момента первого разговора контакта с сотрудником до начала постобработки, значение в секундах</td>
		</tr>
		<tr>
			<td><code>clean_talk_duration</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Чистая длительность разговора. Это только разговоры. Значение в секундах</td>
		</tr>
		<tr>
			<td><code>total_duration</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Длительность разговора. Считается от момента первого разговора контакта с сотрудником до начала постобработки, значение в секундах</td>
		</tr>
		<tr>
			<td><code>postprocess_duration</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Длительность постобработки, значение в секундах</td>
		</tr>
		<tr>
			<td><code>call_records</code></td>
			<td>array</td>
			<td></td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>
				Уникальный идентификатор ссылки на записанный разговор, см. метод <code>"get.call_records"</code>. Можно прослушать вызвав запрос в браузере: <code>http://app.comagic.ru/system/media/talk/{call_session_id}/{record_call_file_link_hash}/</code>
			</td>
		</tr>
		<tr>
			<td><code>voice_mail_records</code></td>
			<td>array</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>
				Уникальный идентификатор ссылки на оставленное голосовое сообщение, см. метод <code>"get.voice_mail_records"</code>. Можно прослушать вызвав запрос в браузере: <code>http://app.comagic.ru/system/media/talk/{call_session_id}/{voice_mail_file_link_hash}/</code>
			</td>
		</tr>
		<tr>
			<td><code>virtual_phone_number</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Виртуальный номер</td>
		</tr>
		<tr>
			<td><code>ua_client_id</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор в Universal Analytics</td>
		</tr>
		<tr>
			<td><code>sale_date</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Дата сделки</td>
		</tr>
		<tr>
			<td><code>sale_cost</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Сумма сделки</td>
		</tr>
		<tr>
			<td><code>is_transfer</code></td>
			<td>boolean</td>
			<td><code>true</code>, <code>false</code></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Был ли трансфер в сессии звонка</td>
		</tr>
		<tr>
			<td><code>search_query</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Поисковый запрос</td>
		</tr>
		<tr>
			<td><code>search_engine</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название поисковой системы</td>
		</tr>
		<tr>
			<td><code>referrer_domain</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Домен реферера</td>
		</tr>
		<tr>
			<td><code>referrer</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Источник перехода</td>
		</tr>
		<tr>
			<td><code>entrance_page</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Страница входа</td>
		</tr>
		<tr>
			<td><code>gclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Google Click Identifier</td>
		</tr>
		<tr>
			<td><code>yclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Yandex Click Identifier</td>
		</tr>
		<tr>
			<td><code>ymclid</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Yandex Market Click Identifier</td>
		</tr>
		<tr>
			<td><code>ef_id</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Используется для разметки ссылок в системе AdLense</td>
		</tr>
		<tr>
			<td><code>channel</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>advert</code></li>
					<li><code>organic</code></li>
					<li><code>referral</code></li>
					<li><code>direct</code></li>
					<li><code>paid</code></li>
					<li><code>display</code></li>
					<li><code>affiliate</code></li>
					<li><code>email</code></li>
					<li><code>social</code></li>
					<li><code>internal</code></li>
				</ul>
			</td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Канал.</td>
		</tr>
		<tr>
			<td colspan="7">Проставленные теги</td>
		</tr>
		<tr>
			<td><code>tags</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Теги, см. метод <code>"get.tags"</code></td>
		</tr>
		<tr>
			<td><code>tag_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор тега</td>
		</tr>
		<tr>
			<td><code>tag_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название тега</td>
		</tr>
		<tr>
			<td><code>tag_change_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Время простановки тега</td>
		</tr>
		<tr>
			<td><code>tag_type</code></td>
			<td>enum</td>
			<td><code>auto</code>, <code>manual</code></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Тип тега</td>
		</tr>
		<tr>
			<td><code>tag_user_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор пользователя, который поставил тег</td>
		</tr>
		<tr>
			<td><code>tag_user_login</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Логин пользователя, который проставил тег</td>
		</tr>
		<tr>
			<td><code>tag_employee_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор сотрудника, который поставил тег</td>
		</tr>
		<tr>
			<td><code>tag_employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Ф.И.О сотрудника, который протсавил тег</td>
		</tr>
		<tr>
			<td colspan="7">Сотрудники участвовавшие в звонке</td>
		</tr>
		<tr>
			<td><code>employees</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Сотрудники, которые участвовали в звонке</td>
		</tr>
		<tr>
			<td><code>employee_id</code></td>
			<td>number</td>
			<td></td>
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
			<td></td>
			<td>Ф.И.О. сотрудника</td>
		</tr>
		<tr>
			<td><code>is_answered</code></td>
			<td>boolean</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Признак, поднял сотрудник трубку или нет</td>
		</tr>
		<tr>
			<td><code>is_talked</code></td>
			<td>boolean</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Признак, участвовал ли сотрудник в разговоре или нет</td>
		</tr>
		<tr>
			<td colspan="7">Последний ответивший сотрудник</td>
		</tr>
		<tr>
			<td><code>last_answered_employee_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор последнего сотрудника, который поднял трубку</td>
		</tr>
		<tr>
			<td><code>last_answered_employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
Ф.И.О последнего сотрудника, который поднял трубку</td>
		</tr>
		<tr>
			<td colspan="7">Первый ответивший сотрудник</td>
		</tr>
		<tr>
			<td><code>first_answered_employee_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор первого сотрудника, который первый поднял трубку</td>
		</tr>
		<tr>
			<td><code>first_answered_employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
Ф.И.О. первого сотрудника, который первый поднял трубку
Последний разговаривавший сотрудник</td>
		</tr>
		<tr>
			<td colspan="7">Последний разговаривавший сотрудник</td>
		</tr>
		<tr>
			<td><code>last_talked_employee_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
Уникальный идентификатор последнего разговаривавшего сотрудника</td>
		</tr>
		<tr>
			<td><code>last_talked_employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Ф.И.О последнего разговаривавшего сотрудника</td>
		</tr>
		<tr>
			<td colspan="7">Первый разговаривавший сотрудник</td>
		</tr>
		<tr>
			<td><code>first_talked_employee_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор первого разговаривавшего сотрудника</td>
		</tr>
		<tr>
			<td><code>first_talked_employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Ф.И.О первого разговаривавшего сотрудника</td>
		</tr>
		<tr>
			<td colspan="7">Сценарий</td>
		</tr>
		<tr>
			<td><code>scenario_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название сценария по которому обрабатывался звонок</td>
		</tr>
		<tr>
			<td><code>scenario_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор сценария по которому обрабатывался звонок</td>
		</tr>
		<tr>
			<td colspan="7">Сайт</td>
		</tr>
		<tr>
			<td><code>site_domain_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Адрес сайта в интернете. Без указания протокола - <code>"http://"</code> или <code>"https://"</code></td>
		</tr>
		<tr>
			<td><code>site_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор сайта</td>
		</tr>
		<tr>
			<td colspan="7">Рекламная кампания</td>
		</tr>
		<tr>
			<td><code>campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название рекламной кампании</td>
		</tr>
		<tr>
			<td><code>campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор рекламной кампании</td>
		</tr>
		<tr>
			<td><code>visit_other_campaign</code></td>
			<td>boolean</td>
			<td><code>true</code>, <code>false</code></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Флаг показывает заходил ли посетитель (в пределах персоны) по другим рекламным кампаниям</td>
		</tr>
		<tr>
			<td colspan="7">Информация о посетителе</td>
		</tr>
		<tr>
			<td><code>visitor_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор посетителя</td>
		</tr>
		<tr>
			<td><code>person_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор персоны</td>
		</tr>
		<tr>
			<td><code>visitor_type</code></td>
			<td>enum</td>
			<td>Новый, Вернувшийся, Не заполнен</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Тип посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_session_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор сессии посетителя</td>
		</tr>
		<tr>
			<td><code>visits_count</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Общее количество посещений посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор первой рекламной <code>"get.campaigns"</code></td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название первой рекламной кампании</td>
		</tr>
		<tr>
			<td><code>visitor_city</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Город посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_region</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Регион посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_country</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Страна посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_device</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>desktop</code></li>
					<li><code>mobile</code></li>
					<li><code>tablet</code></li>
					<li><code>other</code></li>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Устройство пользователя</td>
		</tr>
		<tr>
			<td colspan="7">Свойства посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_custom_properties</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Свойства посетителя, которые могут быть заданы помощью JavaScript API [метод <code>Comagic.setProperty</code>]
			</td>
		</tr>
		<tr>
			<td><code>property_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Имя свойства, которое должно быть присвоено</td>
		</tr>
		<tr>
			<td><code>property_value</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Значение свойства</td>
		</tr>
		<tr>
			<td colspan="7">Сегменты</td>
		</tr>
		<tr>
			<td><code>segments</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Сегменты, см. метод <code>"get.segments"</code></td>
		</tr>
		<tr>
			<td><code>segment_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор сегмента</td>
		</tr>
		<tr>
			<td><code>segment_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название сегмента</td>
		</tr>
		<tr>
			<td>Call API</td>
		</tr>
		<tr>
			<td><code>call_api_request_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Уникальный идентификатор запроса к API, который запросе.
			</td>
		</tr>
		<tr>
			<td><code>call_api_external_id</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Уникальный идентификатор, который может быть события звонка с внешней системой.
			</td>
		</tr>
		<tr>
			<td colspan="7">Контакт из адресной книги</td>
		</tr>
		<tr>
			<td><code>contact_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор контакта</td>
		</tr>
		<tr>
			<td><code>contact_full_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Фамилия Имя Отчество контакта</td>
		</tr>
		<tr>
			<td><code>contact_phone_number</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Номер контакта</td>
		</tr>
		<tr>
			<td colspan="7">UTM-метки</td>
		</tr>
		<tr>
			<td><code>utm_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Источник кампании</td>
		</tr>
		<tr>
			<td><code>utm_medium</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Канал кампании</td>
		</tr>
		<tr>
			<td><code>utm_term</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Ключевое слово кампании</td>
		</tr>
		<tr>
			<td><code>utm_content</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Содержание кампании</td>
		</tr>
		<tr>
			<td><code>utm_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название кампании</td>
		</tr>
		<tr>
			<td colspan="7">OS-метки</td>
		</tr>
		<tr>
			<td><code>openstat_ad</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор рекламного объявления</td>
		</tr>
		<tr>
			<td><code>openstat_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор рекламной кампании</td>
		</tr>
		<tr>
			<td><code>openstat_service</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор сервиса, предоставляющего услуги</td>
		</tr>
		<tr>
			<td><code>openstat_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Идентификатор площадки, раздела, страницы, было показано соответствующее рекламное объявление
			</td>
		</tr>
		<tr>
			<td colspan="7">Атрибуты обращения</td>
		</tr>
		<tr>
			<td><code>attributes</code></td>
			<td>array</td>
			<td>
				<ul>
					<li><code>primary</code> - Первичное</li>
					<li><code>secondary</code> - Вторичное</li>
					<li><code>lost</code> - Потерянное</li>
					<li><code>target</code> - Целевое</li>
					<li><code>off-target</code> - Не целевое</li>
					<li><code>quality</code> - Качественное</li>
					<li><code>rest</code> - целевые повторные обращения (обращения, совершенные в период повторного обращения, настроенного для сайта в ЛК CoMagic).</li>
				</ul>
			</td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Атрибуты обращения</td>
		</tr>
	</tbody>
</table>


### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.calls_report",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "offset":"number",
    "limit":"number",
    "date_from":"string",
    "date_till":"string",
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
        "start_time":"iso8601",
        "finish_time":"iso8601",
        "virtual_phone_number":"number",
        "is_transfer":"boolean",
        "finish_reason":"enum",
        "direction":"enum",
        "source":"enum",
        "communication_number":"number",
        "communication_id":"number",
        "communication_type":"enum",
        "is_lost":"boolean",
        "wait_duration":"number",
        "total_wait_duration":"number",
        "talk_duration":"number",
        "clean_talk_duration":"number",
        "total_duration":"number",
        "postprocess_duration":"number",
        "ua_client_id":"string",
        "sale_date":"iso8601",
        "sale_cost":"number",
        "search_query":"string",
        "search_engine":"string",
        "referrer_domain":"string",
        "referrer":"string",
        "entrance_page":"string",
        "gclid":"string",
        "yclid":"string",
        "ymclid":"string",
        "ef_id":"string",
        "channel":"enum",
        "site_id":"number",
        "site_domain_name":"string",
        "campaign_id":"number",
        "campaign_name":"string",
        "visit_other_campaign":"boolean",
        "visitor_id":"number",
        "person_id":"number",
        "visitor_type":"enum",
        "visitor_session_id":"number",
        "visits_count":"number",
        "visitor_first_campaign_id":"number",
        "visitor_first_campaign_name":"string",
        "visitor_city":"string",
        "visitor_region":"string",
        "visitor_country":"string",
        "visitor_device":"enum",
        "last_answered_employee_id":"number",
        "last_answered_employee_full_name":"string",
        "first_answered_employee_id":"number",
        "first_answered_employee_full_name":"string",
        "scenarion_id":"number",
        "scenarion_name":"string",
        "call_api_external_id":"string",
        "call_api_request_id":"number",
        "contact_phone_number":"string",
        "contact_full_name":"string",
        "contact_id":"number",
        "utm_source":"string",
        "utm_medium":"string",
        "utm_term":"string",
        "utm_content":"string",
        "utm_campaign":"string",
        "openstat_ad":"string",
        "openstat_campaign":"string",
        "openstat_service":"string",
        "openstat_source":"string",
        "attributes":[

        ],
        "call_records":[

        ],
        "voice_mail_records":[

        ],
        "tags":[
          {
            "tag_id":"number",
            "tag_name":"string",
            "tag_type":"enum",
            "tag_change_time":"iso8601",
            "tag_user_id":"number",
            "tag_user_login":"string",
            "tag_employee_id":"number",
            "tag_employee_full_name":"string"
          }
        ],
        "visitor_custom_properties":[
          {
            "property_name":"string",
            "property_value":"string"
          }
        ],
        "segments":[
          {
            "segment_id":"number",
            "segment_name":"string"
          }
        ],
        "employees":[
          {
            "employee_id":"number",
            "employee_full_name":"string",
            "is_answered":"boolean"
          }
        ]
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "Список ошибок для методов с глаголом get"


## `ДОСТУПНО КЛИЕНТАМ` Получение CDR по сессии звонка

Метод | `get.call_legs_report`
:---- | :---------------
Версия API | v2
Описание | Получение списка CDR по сессии звонка
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"
`date_from` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата начала выборки
`date_till` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата окончания выборки

### Параметры ответа

Название | Тип  | Допустимые значения | Фильтрация | Сортировка | Ответ по умолчанию | Описание
:--- | :--- | :--- | :--- | :--- | :--- | :---
`id` | number |  | да |  | да | Уникальный идентификатор CDR
`call_session_id` | number |  | да | да | да | Уникальный идентификатор сессии звонка (см. метод `get.calls_report`)
`call_records` | array |  |  |  | да | Уникальный идентификатор ссылки на записанный разговор, см. метод `"get.call_records"`. Можно прослушать вызвав запрос в браузере: <br>`http://app.comagic.ru/system/media/talk/{call_session_id}/{record_call_file_link}` <blockquote>Берем из `call_session_log` по событие `record_started`</blockquote>
`start_time` | iso8601 | YYYY-MM-DD hh:mm:ss |  | да | да | Дата и время начала плеча
`connect_time` | iso8601 | YYYY-MM-DD hh:mm:ss |  |  | да | Дата и время поднятия трубки
`duration` | number |  | да | да | да | Продолжительность плеча с начала поднятия трубки. Значение в секундах
`total_duration` | number |  | да | да | да | Общая продолжительность плеча. Значение в секундах
`virtual_phone_number` | string |  | да | да | да | Виртуальный номер
`calling_phone_number` | string |  | да | да | да | Номер звонящего
`called_phone_number` | string |  | да | да | да | Номер кому звонили
`direction` | enum | `in`, `out` | да | да | да | Направление плеча
`is_transfered` | boolean | `true`, `false` | да | да | да | Трансферное ли это плечо
`is_operator` | boolean | `true`, `false` | да | да | да | Принадлежит ли это плечо оператору
`employee_id` | number |  | да | да | да | Уникальный идентификатор сотрудника, кому звонили
`employee_full_name` | string |  | да | да |  | Ф.И.О. сотрудника, кому звонили
`employee_phone_number` | string |  | да | да |  | Номер телефона сотрудника
`employee_rating` | number |  | да | да | да | Рейтинг проставленный сотруднику в постобработке
`scenario_id` | number |  | да | да | да | Уникальный идентификатор сценария
`scenario_name` | string |  | да | да |  | Название сценария
`is_coach` | boolean | `true`, `false` | да | да | да | Тренерское ли плечо
`release_cause_code` | number |  | да | да | да | Номер Cause Code (см. Q850)
`release_cause_description` | string |  | да | да | да | Описание cause code
`is_failed` | boolean | `true`, `false` | да | да | да | Поднял ли оператор трубку
`is_talked` | boolean | `true`, `false` | да | да |  | Состоялся ли разговор <blockquote>select * from call_session_log where 332692805 = ANY(cdr_ids) and call_session_id=220757065 and event in ('talk_started', 'transfer_talk_started', 'conference_member_started')</blockquote>
`contact_id` | id |  |  |  |  | Уникальный идентификатор контакта
`contact_full_name` | string |  |  |  |  | Ф.И.О. контакта
`contact_phone_number` | string |  |  |  |  | Телефонный номер контакта <blockquote>Номер контакта (datamart.call_session) = numa</blockquote>

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.call_legs_report",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "offset":"number",
    "limit":"number",
    "date_from":"iso8601",
    "date_till":"iso8601",
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
        "call_session_id":"number",
        "call_records":[

        ],
        "start_time":"iso8601",
        "connect_time":"iso8601",
        "duration":"number",
        "total_duration":"number",
        "virtual_phone_number":"string",
        "calling_phone_number":"string",
        "called_phone_number":"string",
        "direction":"enum",
        "is_transfered":"boolean",
        "is_operator":"boolean",
        "employee_id":"number",
        "employee_full_name":"string",
        "employee_phone_number":"string",
        "employee_rating":"number",
        "scenario_id":"number",
        "scenario_name":"string",
        "is_coach":"boolean",
        "release_cause_code":"number",
        "release_cause_description":"string",
        "is_failed":"boolean",
        "is_talked":"boolean",
        "contact_id":"number",
        "contact_full_name":"string",
        "contact_phone_number":"string"
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "Список ошибок для методов с глаголом get"


## `ДОСТУПНО КЛИЕНТАМ` Получение списка достигнутых целей

Метод | `get.goals_report`
:---- | :---------------
Версия API | v2
Описание | Получение списка достигнутых целей
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"
`date_from` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата начала выборки
`date_till` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата окончания выборки

### Параметры ответа

<table>
	<tbody>
		<tr>
			<th>Название</th>
			<th>Тип</th>
			<th>Допустимые значения</th>
			<th>Фильтрация</th>
			<th>Сортировка</th>
			<th>Ответ по умолчанию</th>
			<th>Описание</th>
		</tr>
		<tr>
			<td><code>id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор цели</td>
		</tr>
		<tr>
			<td><code>date_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Дата и время достижения цели</td>
		</tr>
		<tr>
			<td><code>name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Название цели</td>
		</tr>
		<tr>
			<td><code>communication_number</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Номер обращения. Расcчитывается в
рамках персоны.</td>
		</tr>
		<tr>
			<td><code>communication_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный идентификатор обращения</td>
		</tr>
		<tr>
			<td><code>communication_type</code></td>
			<td>enum</td>
			<td><code>goal</code></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Тип обращения</td>
		</tr>
		<tr>
			<td><code>ua_client_id</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор в Universal Analytics</td>
		</tr>
		<tr>
			<td><code>sale_date</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Дата сделки</td>
		</tr>
		<tr>
			<td><code>sale_cost</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Сумма сделки</td>
		</tr>
		<tr>
			<td><code>search_query</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Поисковый запрос</td>
		</tr>
		<tr>
			<td><code>search_engine</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название поисковой системы</td>
		</tr>
		<tr>
			<td><code>referrer_domain</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Домен реферера</td>
		</tr>
		<tr>
			<td><code>referrer</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Источник перехода</td>
		</tr>
		<tr>
			<td><code>entrance_page</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Страница входа</td>
		</tr>
		<tr>
			<td><code>gclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Google Click Identifier</td>
		</tr>
		<tr>
			<td><code>yclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Yandex Click Identifier</td>
		</tr>
		<tr>
			<td><code>ymclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Yandex Market Click Identifier</td>
		</tr>
		<tr>
			<td><code>ef_id</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Используется для разметки ссылок в
системе управления контекстной
рекламой AdLense</td>
		</tr>
		<tr>
			<td><code>channel</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>advert</code></li>
					<li><code>organic</code></li>
					<li><code>referral</code></li>
					<li><code>direct</code></li>
					<li><code>paid</code></li>
					<li><code>display</code></li>
					<li><code>affiliate</code></li>
					<li><code>email</code></li>
					<li><code>social</code></li>
					<li><code>internal</code></li>
				</ul>
			</td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Канал.</td>
		</tr>
		<tr>
			<td colspan="7">Проставленные теги</td>
		</tr>
		<tr>
			<td><code>tags</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Теги, см. метод <code>"get.tags"</code></td>
		</tr>
		<tr>
			<td><code>tag_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор тега</td>
		</tr>
		<tr>
			<td><code>tag_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название тега</td>
		</tr>
		<tr>
			<td><code>tag_type</code></td>
			<td>enum</td>
			<td><code>auto</code>, <code>manual</code></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Тип тега</td>
		</tr>
		<tr>
			<td><code>tag_change_time</code></td>
			<td>iso8601</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Время простановки тега</td>
		</tr>
		<tr>
			<td><code>tag_user_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор
пользователя, который проставил тег</td>
		</tr>
		<tr>
			<td><code>tag_user_login</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Логин пользователя, который
проставил тег</td>
		</tr>
		<tr>
			<td><code>tag_employee_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор
сотрудника, который проставил тег</td>
		</tr>
		<tr>
			<td><code>tag_employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Ф.И.О. сотрудника, который проставил
тег</td>
		</tr>
		<tr>
			<td colspan="7">Сайт</td>
		</tr>
		<tr>
			<td><code>site_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор сайта</td>
		</tr>
		<tr>
			<td><code>site_domain_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Адрес сайта в интернете. Без указания
протокола - <code>"http://"</code> или <code>"https://"</code></td>
		</tr>
		<tr>
			<td colspan="7">Рекламная кампания</td>
		</tr>
		<tr>
			<td><code>campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор рекламной
кампании</td>
		</tr>
		<tr>
			<td><code>campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Название рекламной кампании</td>
		</tr>
		<tr>
			<td><code>visit_other_campaign</code></td>
			<td>boolean</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Флаг показывает заходил ли
посетитель (в пределах персоны) по
другим рекламным кампаниям</td>
		</tr>
		<tr>
			<td colspan="7">Информация о посетителе</td>
		</tr>
		<tr>
			<td><code>visitor_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор
посетителя</td>
		</tr>
		<tr>
			<td><code>person_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор персоны</td>
		</tr>
		<tr>
			<td><code>visitor_type</code></td>
			<td>enum</td>
			<td>Новый,
Вернувшийся,
Не заполнен</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Тип посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_session_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Уникальный идентификатор сессии
				посетителя, см. <code>"get.visitor_session_report"</code>
			</td>
		</tr>
		<tr>
			<td><code>visits_count</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Общее количество посещений
посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор первой рекламной кампании. См. метод <code>"get.campaigns"</code></td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название первой рекламной кампании</td>
		</tr>
		<tr>
			<td><code>visitor_city</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Город посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_region</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Регион посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_country</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Страна посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_device</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>desktop</code></li>
					<li><code>mobile</code></li>
					<li><code>tablet</code></li>
					<li><code>other</code></li>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Устройство пользователя</td>
		</tr>
		<tr>
			<td colspan="7">Свойства посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_custom_properties</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Свойства посетителя, которые могут
				быть заданы через личный кабинет
				или с помощью JavaScript API [метод <code>Comagic.setProperty(name, value);</code>]
			</td>
		</tr>
		<tr>
			<td><code>property_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Имя свойства, которое должно быть
присвоено посетителю</td>
		</tr>
		<tr>
			<td><code>property_value</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Значение свойства</td>
		</tr>
		<tr>
			<td colspan="7">Сегменты</td>
		</tr>
		<tr>
			<td><code>segments</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Сегменты, см. метод <code>"get.segments"</code></td>
		</tr>
		<tr>
			<td><code>segment_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор сегмента</td>
		</tr>
		<tr>
			<td><code>segment_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название сегмента</td>
		</tr>
		<tr>
			<td colspan="7">UTM-метка</td>
		</tr>
		<tr>
			<td><code>utm_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Источник кампании</td>
		</tr>
		<tr>
			<td><code>utm_medium</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Канал кампании</td>
		</tr>
		<tr>
			<td><code>utm_term</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Ключевое слово кампании</td>
		</tr>
		<tr>
			<td><code>utm_content</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Содержание кампании</td>
		</tr>
		<tr>
			<td><code>utm_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название кампании</td>
		</tr>
		<tr>
			<td colspan="7">OS-метка</td>
		</tr>
		<tr>
			<td><code>openstat_ad</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор рекламного
объявления</td>
		</tr>
		<tr>
			<td><code>openstat_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор рекламной кампании</td>
		</tr>
		<tr>
			<td><code>openstat_service</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор сервиса,
предоставляющего услуги</td>
		</tr>
		<tr>
			<td><code>openstat_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор площадки, раздела,
страницы, места на странице, на
котором было показано
соответствующее рекламное
объявление</td>
		</tr>
		<tr>
			<td colspan="7">Атрибуты обращения</td>
		</tr>
		<tr>
			<td><code>attributes</code></td>
			<td>array</td>
			<td>
				<ul>
					<li><code>primary</code></li>
					<li><code>secondary</code></li>
					<li><code>lost</code></li>
					<li><code>target</code></li>
					<li><code>off-target</code></li>
					<li><code>quality</code></li>
					<li><code>rest</code></li>
				</ul>
			</td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Атрибуты обращения
				<ul>
				<li><code>primary</code> - Первичное</li>
				<li><code>secondary</code> - Вторичное</li>
				<li><code>lost</code> - Потерянное</li>
				<li><code>target</code> - Целевое</li>
				<li><code>off-target</code> - Не целевое</li>
				<li><code>quality</code> - Качественное</li>
				<li><code>rest</code> - целевые повторные
					обращения (обращения,
					совершенные период повторного
					обращения, настроенного для
					сайта в ЛК CoMagic).</li>
				</ul>
			</td>
		</tr>
	</tbody>
</table>


### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.goals_report",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "offset":"number",
    "limit":"number",
    "date_from":"iso8601",
    "date_till":"iso8601",
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
        "date_time":"iso8601",
        "name":"string",
        "communication_number":"number",
        "communication_id":"number",
        "communication_type":"enum",
        "ua_client_id":"string",
        "sale_date":"iso8601",
        "sale_cost":"number",
        "search_query":"string",
        "search_engine":"string",
        "referrer_domain":"string",
        "referrer":"string",
        "entrance_page":"string",
        "gclid":"string",
        "yclid":"string",
        "ymclid":"string",
        "ef_id":"string",
        "channel":"enum",
        "tags":[
          {
            "tag_id":"number",
            "tag_name":"string",
            "tag_type":"enum",
            "tag_change_time":"iso8601",
            "tag_user_id":"number",
            "tag_user_login":"string",
            "tag_employee_id":"number",
            "tag_employee_full_name":"string"
          }
        ],
        "site_id":"number",
        "site_domain_name":"string",
        "campaign_id":"number",
        "campaign_name":"string",
        "visit_other_campaign":"boolean",
        "visitor_id":"number",
        "person_id":"number",
        "visitor_type":"enum",
        "visitor_session_id":"number",
        "visits_count":"number",
        "visitor_first_campaign_id":"number",
        "visitor_first_campaign_name":"string",
        "visitor_city":"string",
        "visitor_region":"string",
        "visitor_country":"string",
        "visitor_device":"enum",
        "visitor_custom_properties":[
          {
            "property_name":"string",
            "property_value":"string"
          }
        ],
        "segments":[
          {
            "segment_id":"number",
            "segment_name":"string"
          }
        ],
        "utm_source":"string",
        "utm_medium":"string",
        "utm_term":"string",
        "utm_content":"string",
        "utm_campaign":"string",
        "openstat_ad":"string",
        "openstat_campaign":"string",
        "openstat_service":"string",
        "openstat_source":"string",
        "attributes":[

        ]
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "Список ошибок для методов с глаголом get"


## `ДОСТУПНО КЛИЕНТАМ` Получение информации о чатах

Метод | `get.chats_report`
:---- | :---------------
Версия API | v2
Описание | Получение информации о чатах
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"
`date_from` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата начала выборки
`date_till` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата конца выборки

### Параметры ответа

<table>
	<tbody>
		<tr>
			<th>Название</th>
			<th>Тип</th>
			<th>Допустимые значения</th>
			<th>Фильтрация</th>
			<th>Сортировка</th>
			<th>Ответ по умолчанию</th>
			<th>Описание</th>
		</tr>
		<tr>
			<td><code>id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный идентификатор чата. Все
сообщения чата можно получить
используя метод <code>"get.chat_messages"</code></td>
		</tr>
		<tr>
			<td><code>status</code></td>
			<td>enum</td>
			<td>
				<code>lost</code> - Потерянный;
				<code>succeed</code> - Состоявшийся;<br>
				<code>refused</code> - Отклоненный
			</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Статус чата</td>
		</tr>
		<tr>
			<td><code>initiator</code></td>
			<td>enum</td>
			<td>Посетитель, Оператор,
Автоприглашение</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Инициатор чата</td>
		</tr>
		<tr>
			<td><code>date_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>Дата и время начала чата</td>
		</tr>
		<tr>
			<td><code>duration</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Продолжительность чата. Значение в
секундах</td>
		</tr>
		<tr>
			<td><code>answer_time</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Время ответа оператора. Значение в
секндах</td>
		</tr>
		<tr>
			<td><code>communication_number</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>
				Номер обращения. Расcчитывается в
				рамках персоны.
			</td>
		</tr>
		<tr>
			<td><code>communication_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный номер обращения</td>
		</tr>
		<tr>
			<td><code>communication_type</code></td>
			<td>enum</td>
			<td><code>chat</code></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Тип обращения</td>
		</tr>
		<tr>
			<td><code>messages_count</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Количество сообщений в чате</td>
		</tr>
		<tr>
			<td><code>ua_client_id</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор в Universal
Analytics</td>
		</tr>
		<tr>
			<td><code>sale_date</code></td>
			<td>iso8601</td>
			<td>YYYY-DD-MM hh:mm:ss</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Дата сделки</td>
		</tr>
		<tr>
			<td><code>sale_cost</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Сумма сделки</td>
		</tr>
		<tr>
			<td><code>is_transfer</code></td>
			<td>boolean</td>
			<td></td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>Был ли чат передан другому
сотруднику</td>
		</tr>
		<tr>
			<td><code>release_cause</code></td>
			<td>enum</td>
			<td>
				<code>closed_by_timeout</code>
				<code>invite_rejected</code>
				<code>closed_by_operator</code>
				<code>closed_by_visitor</code>
				<code>visitor_banned</code>
				<code>external_window_closed</code>
				<code>visitor_disconnected</code>
				<code>visitor_session_expired</code>
			</td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Причина завершения чата</td>
		</tr>
		<tr>
			<td><code>search_query</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Поисковый запрос</td>
		</tr>
		<tr>
			<td><code>search_engine</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название поисковой системы</td>
		</tr>
		<tr>
			<td><code>referrer_domain</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Домен реферера</td>
		</tr>
		<tr>
			<td><code>referrer</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Источник перехода</td>
		</tr>
		<tr>
			<td><code>entrance_page</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Страница входа</td>
		</tr>
		<tr>
			<td><code>gclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Google Click Identifier</td>
		</tr>
		<tr>
			<td><code>yclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Yandex Click Identifier</td>
		</tr>
		<tr>
			<td><code>ymclid</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Yandex Market Click Identifier</td>
		</tr>
		<tr>
			<td><code>ef_id</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Используется для разметки ссылок в
системе управления контекстной
рекламой AdLense</td>
		</tr>
		<tr>
			<td><code>channel</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>advert</code></li>
					<li><code>organic</code></li>
					<li><code>referral</code></li>
					<li><code>direct</code></li>
					<li><code>paid</code></li>
					<li><code>display</code></li>
					<li><code>affiliate</code></li>
					<li><code>email</code></li>
					<li><code>social</code></li>
					<li><code>internal</code></li>
				</ul>
			</td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Канал.
				<ul>
				<li><code>display</code> - Баннерная реклама. Переходы по клику на баннер с рекламой с определенными UTM-метками (<code>display</code>, <code>cpm</code>, <code>banner</code> и др.), размещенной на сторонних сайтах;</li>
				<li><code>paid</code> - Платная реклама. Переходы с рекламных объявлений Google AdWords, Яндекс.Директ и Бегун, c торговых площадок Яндекс.Маркет и Aport или с метками UTM или Openstat (<code>cpc</code>, <code>ppc</code>, <code>cpv</code> и др.);</li>
				<li><code>affiliate</code> - Партнерские программы. Переходы с рекламы, размещенной в партнерских сетях, содержащей определенные UTM-метки (<code>admitad</code>, <code>gdeslon</code> и др.);</li>
				<li><code>social</code> - Социальные сети. Переходы по ссылке, размещенной в ВКонтакте или Facebook или содержащей определенные UTM-метки (<code>social</code>, <code>smm</code> и др.);</li>
				<li><code>email</code> - Почтовая рассылка. Переходы по ссылке, размещенной в email-рассылке и содержащей определенные метки UTM или Openstat (email или e-mail);</li>
				<li><code>organic</code> - Поисковые сети. Переходы по ссылкам со страниц поисковой выдачи;</li>
				<li><code>direct</code> - Прямые заходы. Переходы по введенному URL в адресной строке или через закладку в браузере;</li>
				<li><code>internal</code> - Внутренние переходы. Переходы, совершенные по окончании сессии (30 минут неактивности) или со страницы вашего сайта, на которой не установлен код нашего сервиса;</li>
				<li><code>referral</code> - Переходы по ссылке. Переходы, совершенные по ссылке, размещенной на сторонних сайтах.</li>
				</ul>
			</td>
		</tr>
		<tr>
			<td colspan="7">Сотрудник принявший чат</td>
		</tr>
		<tr>
			<td><code>employee_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор
сотрудника</td>
		</tr>
		<tr>
			<td><code>employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Фамилия Имя Сотрудника</td>
		</tr>
		<tr>
			<td><code>employee_raiting</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>Рейтинг оператора выставленный
посетителем</td>
		</tr>
		<tr>
			<td><code>employee_messages_count</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Количество сообщений оператора в
чате</td>
		</tr>
		<tr>
			<td colspan="7">Проставленные теги</td>
		</tr>
		<tr>
			<td><code>tags</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Теги, см. метод <code>"get.tags"</code></td>
		</tr>
		<tr>
			<td><code>tag_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор тега</td>
		</tr>
		<tr>
			<td><code>tag_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название тега</td>
		</tr>
		<tr>
			<td><code>tag_change_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Время простановки тега</td>
		</tr>
		<tr>
			<td><code>tag_type</code></td>
			<td>enum</td>
			<td><code>auto</code>, <code>manual</code></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Тип тега</td>
		</tr>
		<tr>
			<td><code>tag_user_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор
пользователя, который проставил тег</td>
		</tr>
		<tr>
			<td><code>tag_user_login</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Логин пользователя проставившего тег</td>
		</tr>
		<tr>
			<td><code>tag_employee_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор
сотрудника, который проставил тег</td>
		</tr>
		<tr>
			<td><code>tag_employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Ф.И.О сотрудника, который проставил
тег</td>
		</tr>
		<tr>
			<td colspan="7">Сайт</td>
		</tr>
		<tr>
			<td><code>site_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор сайта</td>
		</tr>
		<tr>
			<td><code>site_domain_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Адрес сайта в интернете. Без указания
протокола - <code>"http://"</code> или <code>"https://"</code></td>
		</tr>
		<tr>
			<td colspan="7">Рекламная кампания</td>
		</tr>
		<tr>
			<td><code>campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор рекламной
кампании</td>
		</tr>
		<tr>
			<td><code>campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название рекламной кампании</td>
		</tr>
		<tr>
			<td><code>visit_other_campaign</code></td>
			<td>boolean</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Флаг показывает заходил ли
посетитель (в пределах персоны) по
другим рекламным кампаниям</td>
		</tr>
		<tr>
			<td colspan="7">Информация о посетителе</td>
		</tr>
		<tr>
			<td><code>visitor_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор
посетителя</td>
		</tr>
		<tr>
			<td><code>person_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор персоны</td>
		</tr>
		<tr>
			<td><code>visitor_type</code></td>
			<td>enum</td>
			<td>Новый, Вернувшийся, Не
заполнен</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Тип посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_session_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор сессии посетителя, см. <code>"get.visitor_session_report"</code></td>
		</tr>
		<tr>
			<td><code>visits_count</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Общее количество посещений
посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор первой рекламной кампании. См. метод <code>"get.campaigns"</code></td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название первой рекламной кампании</td>
		</tr>
		<tr>
			<td><code>visitor_city</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Город посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_region</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Регион посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_country</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Страна посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_device</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>desktop</code></li>
					<li><code>mobile</code></li>
					<li><code>tablet</code></li>
					<li><code>other</code></li>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Устройство посетителя</td>
		</tr>
		<tr>
			<td colspan="7">Свойства посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_custom_properties</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Свойства посетителя, которые могут
				быть заданы через личный кабинет
				или с помощью JavaScript API [метод
				<code>Comagic.setProperty(name, value);</code>]
			</td>
		</tr>
		<tr>
			<td><code>property_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Имя свойства, которое должно быть
присвоено посетителю</td>
		</tr>
		<tr>
			<td><code>property_value</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Значение свойства</td>
		</tr>
		<tr>
			<td colspan="7">Сегменты</td>
		</tr>
		<tr>
			<td><code>segments</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Сегменты, см. метод <code>"get.segments"</code></td>
		</tr>
		<tr>
			<td><code>segment_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор сегмента</td>
		</tr>
		<tr>
			<td><code>segment_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название сегмента</td>
		</tr>
		<tr>
			<td colspan="7">UTM-метки</td>
		</tr>
		<tr>
			<td><code>utm_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Источник кампании</td>
		</tr>
		<tr>
			<td><code>utm_medium</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Канал кампании</td>
		</tr>
		<tr>
			<td><code>utm_term</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Ключевое слово кампании</td>
		</tr>
		<tr>
			<td><code>utm_content</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Содержание кампании</td>
		</tr>
		<tr>
			<td><code>utm_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название кампании</td>
		</tr>
		<tr>
			<td colspan="7">OS-метки</td>
		</tr>
		<tr>
			<td><code>openstat_ad</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор рекламного
объявления</td>
		</tr>
		<tr>
			<td><code>openstat_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор рекламной кампании</td>
		</tr>
		<tr>
			<td><code>openstat_service</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор сервиса,
предоставляющего услуги</td>
		</tr>
		<tr>
			<td><code>openstat_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор площадки, раздела,
страницы, места на странице, на
котором было показано
соответствующее рекламное
объявление</td>
		</tr>
		<tr>
			<td colspan="7">Атрибуты обращения</td>
		</tr>
		<tr>
			<td><code>attributes</code></td>
			<td>array</td>
			<td>
				<ul>
					<li><code>primary</code></li>
					<li><code>secondary</code></li>
					<li><code>lost</code></li>
					<li><code>target</code></li>
					<li><code>off-target</code></li>
					<li><code>quality</code></li>
					<li><code>rest</code></li>
				</ul>
			</td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
					Атрибуты обращения
				<ul>
					<li><code>primary</code> - Первичное</li>
					<li><code>secondary</code> - Вторичное</li>
					<li><code>lost</code> - Потерянное</li>
					<li><code>target</code> - Целевое</li>
					<li><code>off-target</code> - Не целевое</li>
					<li><code>quality</code> - Качественное</li>
					<li><code>rest</code> - целевые повторные обращения (обращения, совершенные в период повторного обращения, настроенного для сайта в ЛК CoMagic).</li>
				</ul>
			</td>
		</tr>
	</tbody>
</table>


### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.chat_report",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "date_from":"iso8601",
    "date_till":"iso8601",
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
        "status":"enum",
        "initiator":"enum",
        "date_time":"iso8601",
        "duration":"string",
        "answer_time":"number",
        "communication_number":"number",
        "communication_id":"number",
        "communication_type":"enum",
        "messages_count":"number",
        "ua_client_id":"string",
        "sale_date":"iso8601",
        "sale_cost":"number",
        "is_transfer":"boolean",
        "release_cause":"enum",
        "search_query":"string",
        "search_engine":"string",
        "referrer_domain":"string",
        "referrer":"string",
        "entrance_page":"string",
        "gclid":"string",
        "yclid":"string",
        "ymclid":"string",
        "ef_id":"string",
        "channel":"enum",
        "employee_id":"number",
        "employee_full_name":"string",
        "employee_messages_count":"number",
        "employee_raiting":"number",
        "site_id":"number",
        "site_domain_name":"string",
        "campaign_id":"number",
        "campaign_name":"string",
        "visit_other_campaign":"boolean",
        "visitor_id":"number",
        "person_id":"number",
        "visitor_type":"enum",
        "visitor_session_id":"number",
        "visits_count":"number",
        "visitor_first_campaign_id":"number",
        "visitor_first_campaign_name":"string",
        "visitor_city":"string",
        "visitor_region":"string",
        "visitor_country":"string",
        "visitor_device":"enum",
        "utm_source":"string",
        "utm_medium":"string",
        "utm_term":"string",
        "utm_content":"string",
        "utm_campaign":"string",
        "openstat_ad":"string",
        "openstat_campaign":"string",
        "openstat_service":"string",
        "openstat_source":"string",
        "attributes":[

        ],
        "visitor_custom_properties":[
          {
            "property_name":"string",
            "property_value":"string"
          }
        ],
        "segments":[
          {
            "segment_id":"number",
            "segment_name":"string"
          }
        ],
        "tags":[
          {
            "tag_id":"number",
            "tag_name":"string",
            "tag_type":"enum",
            "tag_change_time":"iso8601",
            "tag_user_login":"string",
            "tag_user_id":"number",
            "tag_employee_id":"number",
            "tag_employee_full_name":"string"
          }
        ]
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "Список ошибок для методов с глаголом get"


## `ДОСТУПНО КЛИЕНТАМ` Получение всех сообщений чата

Метод | `get.chat_messages_report`
:---- | :---------------
Версия API | v2
Описание | Получение всех сообщений чата
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"
`chat_id` | number | да |  | Уникальный идентификатор чата

### Параметры ответа

<table>
	<tbody>
		<tr>
			<th>Название</th>
			<th>Тип</th>
			<th>Допустимые значения</th>
			<th>Фильтрация</th>
			<th>Сортировка</th>
			<th>Ответ по
умолчанию</th>
			<th>Описание</th>
		</tr>
		<tr>
			<td><code>chat_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>
				Уникальный идентификатор чата, см.
				метод <code>"get.chats_report"</code>
			</td>
		</tr>
		<tr>
			<td><code>date_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>
				Дата и время когда было отправлено
сообщение <blockquote>Все сообщения должны быть
в порядке их отправки, т.е
отсортированы по полю
<code>"date_time"</code></blockquote>
			</td>
		</tr>
		<tr>
			<td><code>text</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>Текст сообщения</td>
		</tr>
		<tr>
			<td><code>source</code></td>
			<td>enum</td>
			<td>Оператор,
Посетитель, Автопри
глашение</td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>Источник сообщения</td>
		</tr>
		<tr>
			<td colspan="7">Сотрудник</td>
		</tr>
		<tr>
			<td><code>employee_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор сотрудника</td>
		</tr>
		<tr>
			<td><code>employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>Фамилия Имя Отчество сотрудника</td>
		</tr>
	</tbody>
</table>


### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.chat_messages_report",
  "params":{
    "access_token":"string",
    "chat_id":"number",
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
        "chat_id":"number",
        "date_time":"iso8601",
        "text":"string",
        "source":"enum",
        "employee_id":"number",
        "employee_full_name":"string"
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "Список ошибок для методов с глаголом get"


## `ДОСТУПНО КЛИЕНТАМ` Получение информации по оффлайн заявкам

Метод | `get.offline_messages_report`
:---- | :---------------
Версия API | v2
Описание | Получение информации по оффлайн заявкам
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"
`date_from` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата начала выборки
`date_till` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата окончания выборки

### Параметры ответа

<table>
	<tbody>
		<tr>
			<th>Название</th>
			<th>Тип</th>
			<th>Допустимые значения</th>
			<th>Фильтрация</th>
			<th>Сортировка</th>
			<th>Ответ по умолчанию</th>
			<th>Описание</th>
		</tr>
		<tr>
			<td><code>id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный идентификатор
оффлайн заявки</td>
		</tr>
		<tr>
			<td><code>date_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Дата и время получения заявки</td>
		</tr>
		<tr>
			<td><code>text</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>Текст заявки</td>
		</tr>
		<tr>
			<td><code>communication_number</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Номер обращения.
Расcчитывается в рамках
персоны.</td>
		</tr>
		<tr>
			<td><code>communication_type</code></td>
			<td>enum</td>
			<td><code>offline_message</code></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Тип обращения</td>
		</tr>
		<tr>
			<td><code>communication_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный идентификатор
обращения</td>
		</tr>
		<tr>
			<td><code>ua_client_id</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор в
Universal Analytics</td>
		</tr>
		<tr>
			<td><code>sale_date</code></td>
			<td>iso8601</td>
			<td>YYY-MM-DD
hh:mm:ss</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Дата сделки</td>
		</tr>
		<tr>
			<td><code>sale_cost</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Сумма сделки</td>
		</tr>
		<tr>
			<td><code>status</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>processing</code></li>
					<li><code>processed</code></li>
					<li><code>not_processed</code></li>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Статус заявки</td>
		</tr>
		<tr>
			<td><code>process_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD
hh:mm:ss</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Дата и время, когда заявка была
переведена в статус "Обработано"
(см. параметр <code>"status"</code>)</td>
		</tr>
		<tr>
			<td><code>form_type</code></td>
			<td>enum</td>
			<td>Пользовательская,
Стандартная</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Тип формы с которой была
отправлена оффлайн заявка</td>
		</tr>
		<tr>
			<td><code>search_query</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Поисковый запрос</td>
		</tr>
		<tr>
			<td><code>search_engine</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название поисковой системы</td>
		</tr>
		<tr>
			<td><code>referrer_domain</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Домен реферера</td>
		</tr>
		<tr>
			<td><code>referrer</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Источник перехода</td>
		</tr>
		<tr>
			<td><code>entrance_page</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Страница входа</td>
		</tr>
		<tr>
			<td><code>gclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Google Click Identifier</td>
		</tr>
		<tr>
			<td><code>yclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Yandex Click Identifier</td>
		</tr>
		<tr>
			<td><code>ymclid</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Yandex Market Click Identifier</td>
		</tr>
		<tr>
			<td><code>ef_id</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Используется для разметки
ссылок в системе управления
контекстной рекламой AdLense</td>
		</tr>
		<tr>
			<td><code>channel</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>advert</code></li>
					<li><code>organic</code></li>
					<li><code>referral</code></li>
					<li><code>direct</code></li>
					<li><code>paid</code></li>
					<li><code>display</code></li>
					<li><code>affiliate</code></li>
					<li><code>email</code></li>
					<li><code>social</code></li>
					<li><code>internal</code></li>
				</ul>
			</td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Канал.</td>
		</tr>
		<tr>
			<td colspan="7">Группа, выбранная посетителем</td>
		</tr>
		<tr>
			<td><code>group_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор
группы, выбранной постетителем</td>
		</tr>
		<tr>
			<td><code>group_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Название группы, выбранной
посетителем</td>
		</tr>
		<tr>
			<td colspan="7">Сотрудник</td>
		</tr>
		<tr>
			<td><code>employee_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор
сотрудника, который обработал
заявку</td>
		</tr>
		<tr>
			<td><code>employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Фамилия Имя Сотрудника,
который обработал заявку</td>
		</tr>
		<tr>
			<td><code>employee_answer_message</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Ответ сотрудника, который был
отправлен на адрес электронной
почты посетителя</td>
		</tr>
		<tr>
			<td><code>employee_comment</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Комментарий сотрудника при
переводе заявки в статус
"Обработано" (см. поле <code>"status"</code>)</td>
		</tr>
		<tr>
			<td colspan="7">Проставленные теги</td>
		</tr>
		<tr>
			<td><code>tags</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Теги, см. метод <code>"get.tags"</code></td>
		</tr>
		<tr>
			<td><code>tag_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор тега</td>
		</tr>
		<tr>
			<td><code>tag_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название тега</td>
		</tr>
		<tr>
			<td><code>tag_change_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD
hh:mm:ss</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Время простановки тега</td>
		</tr>
		<tr>
			<td><code>tag_type</code></td>
			<td>enum</td>
			<td><code>auto</code>, <code>manual</code></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Тип тега</td>
		</tr>
		<tr>
			<td><code>tag_user_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор
пользователя, который проставил
тег</td>
		</tr>
		<tr>
			<td><code>tag_user_login</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Логин пользователя, который
проставил тег</td>
		</tr>
		<tr>
			<td><code>tag_employee_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор
сотрудника, который проставил
тег</td>
		</tr>
		<tr>
			<td><code>tag_employee_full_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Ф.И.О. сотрудника, который
проставил тег</td>
		</tr>
		<tr>
			<td colspan="7">Сайт</td>
		</tr>
		<tr>
			<td><code>site_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор сайта</td>
		</tr>
		<tr>
			<td><code>site_domain_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Адрес сайта в интернете. Без
				указания протокола - <code>"http://"</code> или
				<code>"https://"</code>
			</td>
		</tr>
		<tr>
			<td colspan="7">Рекламная кампания</td>
		</tr>
		<tr>
			<td><code>campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор
рекламной кампании</td>
		</tr>
		<tr>
			<td><code>campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название рекламной кампании</td>
		</tr>
		<tr>
			<td><code>visit_other_campaign</code></td>
			<td>boolean</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Флаг показывает заходил ли
посетитель (в пределах персоны)
по другим рекламным кампаниям</td>
		</tr>
		<tr>
			<td colspan="7">Информация о посетителе</td>
		</tr>
		<tr>
			<td><code>visitor_phone_number</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Номер телефона посетителя
оставленный в заявке</td>
		</tr>
		<tr>
			<td><code>visitor_email</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Адрес электронной почты
оставленный посетителем</td>
		</tr>
		<tr>
			<td><code>visitor_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Имя, которое оставил посетитель
при подаче заявки</td>
		</tr>
		<tr>
			<td><code>visitor_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор посетителя</td>
		</tr>
		<tr>
			<td><code>person_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор
персоны</td>
		</tr>
		<tr>
			<td><code>visitor_type</code></td>
			<td>enum</td>
			<td>Новый,
Вернувшийся, Не
заполнен</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Тип посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_session_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный идентификатор
сессии посетителя, см. <code>"get.visitor_session_report"</code></td>
		</tr>
		<tr>
			<td><code>visits_count</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Общее количество посещений
посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор
первой рекламной кампании. См.
метод <code>"get.campaigns"</code></td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название первой рекламной
кампании</td>
		</tr>
		<tr>
			<td><code>visitor_city</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Город посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_country</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Страна посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_region</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Регион посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_device</code></td>
			<td>enum</td>
			<td>
				<ul>
					<code>desktop</code>
					<code>mobile</code>
					<code>tablet</code>
					<code>other</code>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Устройство посетителя</td>
		</tr>
		<tr>
			<td colspan="7">Свойства посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_custom_properties</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Свойства посетителя, которые
				могут быть заданы через личный
				кабинет или с помощью JavaScript
				API [метод
				<code>Comagic.setProperty(name, value);</code>]
			</td>
		</tr>
		<tr>
			<td><code>property_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Имя свойства, которое должно
быть присвоено посетителю</td>
		</tr>
		<tr>
			<td><code>property_value</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Значение свойства</td>
		</tr>
		<tr>
			<td colspan="7">Сегменты</td>
		</tr>
		<tr>
			<td><code>segments</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Сегменты, см. метод <code>"get.segments"</code></td>
		</tr>
		<tr>
			<td><code>segment_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор
сегмента</td>
		</tr>
		<tr>
			<td><code>segment_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название сегмента</td>
		</tr>
		<tr>
			<td colspan="7">UTM-метки</td>
		</tr>
		<tr>
			<td><code>utm_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Источник кампании</td>
		</tr>
		<tr>
			<td><code>utm_medium</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Канал кампании</td>
		</tr>
		<tr>
			<td><code>utm_term</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Ключевое слово кампании</td>
		</tr>
		<tr>
			<td><code>utm_content</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Содержание кампании</td>
		</tr>
		<tr>
			<td><code>utm_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название кампании</td>
		</tr>
		<tr>
			<td colspan="7">OS-метки</td>
		</tr> 
		<tr>
			<td><code>openstat_ad</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор рекламного
объявления</td>
		</tr>
		<tr>
			<td><code>openstat_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор рекламной
кампании</td>
		</tr>
		<tr>
			<td><code>openstat_service</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор сервиса,
предоставляющего услуги</td>
		</tr>
		<tr>
			<td><code>openstat_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор площадки,
раздела, страницы, места на
странице, на котором было
показано соответствующее
рекламное объявление</td>
		</tr>
		<tr>
			<td colspan="7">Атрибуты обращения</td>
		</tr>
		<tr>
			<td><code>attributes</code></td>
			<td>array</td>
			<td>
				<ul>
					<li><code>primary</code></li>
					<li><code>secondary</code></li>
					<li><code>lost</code></li>
					<li><code>target</code></li>
					<li><code>off-target</code></li>
					<li><code>quality</code></li>
				</ul>
			</td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
					Атрибуты обращения
				<ul>
					<li><code>primary</code> - Первичное</li>
					<li><code>secondary</code> - Вторичное</li>
					<li><code>lost</code> - Потерянное</li>
					<li><code>target</code> - Целевое</li>
					<li><code>off-target</code> - Не целевое</li>
					<li><code>quality</code> - Качественное</li>
					<li><code>rest</code> - целевые повторные обращения (обращения, совершенные в период повторного обращения, настроенного для сайта в ЛК CoMagic).</li>
				</ul>
			</td>
		</tr>
	</tbody>
</table>


### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.offline_messages_report",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "offset":"number",
    "limit":"number",
    "date_from":"iso8601",
    "date_till":"iso8601",
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
        "date_time":"iso8601",
        "text":"string",
        "communication_number":"number",
        "communication_type":"enum",
        "communication_id":"number",
        "ua_client_id":"string",
        "sale_date":"iso8601",
        "sale_cost":"number",
        "status":"enum",
        "process_time":"iso8601",
        "form_type":"enum",
        "search_query":"string",
        "search_engine":"string",
        "referrer_domain":"string",
        "referrer":"string",
        "entrance_page":"string",
        "gclid":"string",
        "yclid":"string",
        "ymclid":"string",
        "ef_id":"string",
        "channel":"enum",
        "employee_id":"number",
        "employee_full_name":"string",
        "employee_answer_message":"string",
        "employee_comment":"string",
        "tags":[
          {
            "tag_id":"number",
            "tag_name":"string",
            "tag_type":"enum",
            "tag_change_time":"iso8601",
            "tag_user_id":"number",
            "tag_user_login":"string",
            "tag_employee_id":"number",
            "tag_employee_full_name":"string"
          }
        ],
        "site_id":"number",
        "site_domain_name":"string",
        "group_id":"number",
        "group_name":"string",
        "campaign_id":"number",
        "campaign_name":"string",
        "visit_other_campaign":"boolean",
        "visitor_id":"number",
        "visitor_name":"string",
        "visitor_phone_number":"number",
        "visitor_email":"string",
        "person_id":"number",
        "visitor_type":"enum",
        "visitor_session_id":"number",
        "visits_count":"number",
        "visitor_first_campaign_id":"number",
        "visitor_first_campaign_name":"string",
        "visitor_city":"string",
        "visitor_region":"string",
        "visitor_country":"string",
        "visitor_device":"enum",
        "visitor_custom_properties":[
          {
            "property_name":"string",
            "property_value":"string"
          }
        ],
        "segments":[
          {
            "segment_id":"number",
            "segment_name":"string"
          }
        ],
        "utm_source":"string",
        "utm_medium":"string",
        "utm_term":"string",
        "utm_content":"string",
        "utm_campaign":"string",
        "openstat_ad":"string",
        "openstat_campaign":"string",
        "openstat_service":"string",
        "openstat_source":"string",
        "attributes":[

        ]
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "Список ошибок для методов с глаголом get"


## `ДОСТУПНО КЛИЕНТАМ` Получение информации о сессии посетителя

Метод | `get.visitor_sessions_report`
:---- | :---------------
Версия API | v2
Описание | Получение информации о сессии посетителя
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"
`date_from` | iso8601 | да |  | Дата начала выборки
`date_till` | iso8601 | да |  | Дата окончания выборки

### Параметры ответа

<table>
	<tbody>
		<tr>
			<th>Название</th>
			<th>Тип</th>
			<th>Допустимые значения</th>
			<th>Фильтрация</th>
			<th>Сортировка</th>
			<th>Ответ по умолчанию</th>
			<th>Описание</th>
		</tr>
		<tr>
			<td><code>date_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD
hh:mm:ss</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Дата и время сессии</td>
		</tr>
		<tr>
			<td>
				<code>id</code>
			</td>
				<td>number</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Уникальный идентификатор сессии</td>
		</tr>
		<tr>
			<td>
				<code>ua_client_id</code>
			</td>
				<td>string</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Уникальный идентификатор в
Universal Analytics</td>
		</tr>
		<tr>
			<td>
				<code>gclid</code>
			</td>
				<td>string</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Значение метки <code>gclid</code></td>
		</tr>
		<tr>
			<td>
				<code>yclid</code>
			</td>
				<td>string</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Значение метки <code>yclid</code></td>
		</tr>
		<tr>
			<td>
				<code>ef_id</code>
			</td>
				<td>string</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Значение метки <code>ef_id</code></td>
		</tr>
		<tr>
			<td>
				<code>ymclid</code>
			</td>
				<td>string</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Значение метки <code>ymclid</code></td>
		</tr>
		<tr>
			<td>
				<code>referrer_domain</code>
			</td>
				<td>string</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Домен реферера</td>
		</tr>
		<tr>
			<td>
				<code>referrer</code>
			</td>
				<td>string</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Источник перехода</td>
		</tr>
		<tr>
			<td>
				<code>search_engine</code>
			</td>
				<td>string</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Поисковая система</td>
		</tr>
		<tr>
			<td>
				<code>search_query</code>
			</td>
				<td>string</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Поисковый запрос</td>
		</tr>
		<tr>
			<td>
				<code>entrance_page</code>
			</td>
				<td>string</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Страница входа</td>
		</tr>
		<tr>
			<td>
				<code>exit_page</code>
			</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Страница выхода</td>
		</tr>
		<tr>
			<td>
				<code>duration</code>
			</td>
				<td>number</td>
				<td></td>
				<td></td>
				<td></td>
				<td></td>
				<td>Продолжительность сессии.
Значение в секундах</td>
		</tr>
		<tr>
			<td>
				<code>channel</code>
			</td>
				<td>enum</td>
				<td>
					<ul>
						<li><code>advert</code></li>
						<li><code>organic</code></li>
						<li><code>referral</code></li>
						<li><code>direct</code></li>
						<li><code>paid</code></li>
						<li><code>display</code></li>
						<li><code>affiliate</code></li>
						<li><code>email</code></li>
						<li><code>social</code></li>
						<li><code>internal</code></li>
					</ul>
				</td>
				<td></td>
				<td></td>
				<td></td>
				<td>Канал.</td>
		</tr>
		<tr>
			<td>
				<code>engine</code>
			</td>
				<td>enum</td>
				<td>
					<ul>
						<li><code>yandex.metrika</code></li>
						<li><code>yandex.direct</code></li>
						<li><code>google.analytics</code></li>
						<li><code>google.adwords</code></li>
					</ul>
				</td>
				<td></td>
				<td></td>
				<td></td>
				<td>
					Платформа для рекламной кампании
					<code>pcc.engine_mnemonic</code>
				</td>
		</tr>
		<tr>
			<td colspan="7">
				Рекламная кампания
			</td>
		</tr>
		<tr>
			<td><code>campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор
рекламной кампании</td>
		</tr>
		<tr>
			<td><code>campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Название рекламной кампании</td>
		</tr>
		<tr>
			<td colspan="7">Сайт</td>
		</tr>
		<tr>
			<td><code>site_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор сайта</td>
		</tr>
		<tr>
			<td><code>site_domain_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Адрес сайта в интернете. Без указания протокола - <code>"http://"</code> или <code>"https://"</code></td>
		</tr>
		<tr>
			<td colspan="7">Информация о посетителе</td>
		</tr>
		<tr>
			<td><code>visitor_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор
посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_device</code></td>
			<td>enum</td>
			<td>
				<ul>
					<code>desktop</code>
					<code>mobile</code>
					<code>tablet</code>
					<code>other</code>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Устройство посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_country</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Страна посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_city</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Город посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_region</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Регион посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_ip_address</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>IP-адрес посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_type</code></td>
			<td>enum</td>
			<td>Новый,
Вернувшийся</td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Тип посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_browser_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Браузер посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_browser_version</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Версия браузера посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_os_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Название операционной системы
посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_os_version</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Версия операционной системы
посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_provider</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Интернет провайдер посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_screen</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Разрешение монитора посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_language</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Локализация устройства посетителя</td>
		</tr>
		<tr>
			<td colspan="7">Свойства посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_custom_properties</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Свойства посетителя, которые могут
				быть заданы через личный кабинет
				или с помощью JavaScript API [мето
				д <code>Comagic.setProperty(name, value);</code>]
			</td>
		</tr>
		<tr>
			<td><code>property_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Имя свойства, которое должно быть
присвоено посетителю</td>
		</tr>
		<tr>
			<td><code>property_value</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Значение свойства</td>
		</tr>
		<tr>
			<td colspan="7">UTM-метки</td>
		</tr>
		<tr>
			<td><code>utm_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>UTM-source</td>
		</tr>
		<tr>
			<td><code>utm_medium</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>UTM-medium</td>
		</tr>
		<tr>
			<td><code>utm_term</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>UTM-term</td>
		</tr>
		<tr>
			<td><code>utm_content</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>UTM-content</td>
		</tr>
		<tr>
			<td><code>utm_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>UTM-campaign</td>
		</tr>
		<tr>
			<td colspan="7">Openstat-метки</td>
		</tr>
		<tr>
			<td><code>openstat_ad</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор рекламного
объявления</td>
		</tr>
		<tr>
			<td><code>openstat_campaign</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор рекламной кампании</td>
		</tr>
		<tr>
			<td><code>openstat_service</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор сервиса,
предоставляющего услуги</td>
		</tr>
		<tr>
			<td><code>openstat_source</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Идентификатор площадки, раздела,
страницы, места на странице, на
котором было показано
соответствующее рекламное
объявление</td>
		</tr>
		<tr>
			<td colspan="7">Список посещённых страниц</td>
		</tr>
		<tr>
			<td><code>hits_count</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Количество посещенных страниц</td>
		</tr>
		<tr>
			<td><code>hits</code></td>
			<td>array</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Список посещённых страниц</td>
		</tr>
		<tr>
			<td><code>hit_time</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Время перехода на страниц</td>
		</tr>
		<tr>
			<td><code>hit_duration</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Длительность посещения страницы.
Формат <code>"HH:MM:SS"</code></td>
		</tr>
		<tr>
			<td><code>hit_url</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Адрес страницы</td>
		</tr>
		<tr>
			<td colspan="7">Список сегментов</td>
		</tr>
		<tr>
			<td><code>segments</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Сегменты, см. метод <code>"get.segments"</code></td>
		</tr>
		<tr>
			<td><code>segment_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название сегмента</td>
		</tr>
		<tr>
			<td><code>segment_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор сегмента</td>
		</tr>
		<tr>
			<td colspan="7">Список обращений</td>
		</tr>
		<tr>
			<td><code>communications</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Тип обращения, см. метод <code>"get.communications_report"</code>
			</td>
		</tr>
		<tr>
			<td><code>communication_type</code></td>
			<td>enum</td>
			<td><code>chat</code>, <code>call</code>, <code>goal</code>, <code>offline_message</code></td>
			<td></td>
			<td></td>
			<td></td>
			<td>
				Тип обращения. Для получения
				детализированной информации по
				каждому типу обращения можно
				использовать следующие методы: <code>"get.communications_report"</code>, <code>"get.chats_report"</code>, <code>"get.goals_report"</code>, <code>"get.offline_messages_report"</code>, <code>"get.calls_report"</code>
			</td>
		</tr>
		<tr>
			<td><code>communication_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>
				Уникальный идентификатор
				обращения. По данному
				идентификатору можно получить
				детализированную информацию
				используя следующие методы: <code>"get.communications_report"</code>, <code>"get.chats_report "</code>, <code>"get.goals_report "</code>, <code>"get.offline_messages_report "</code>, <code>"get.calls_report"</code>
			</td>
		</tr>
		<tr>
			<td><code>communication_date_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Дата и время обращения</td>
		</tr>
	</tbody>
</table>
 

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.visitor_sessions_report",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "offset":"number",
    "limit":"number",
    "date_from":"iso8601",
    "date_till":"iso8601",
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
        "date_time":"iso8601",
        "gclid":"string",
        "ua_client_id":"string",
        "yclid":"string",
        "ef_id":"string",
        "ymclid":"string",
        "engine":"enum",
        "referrer_domain":"string",
        "referrer":"string",
        "search_engine":"string",
        "search_query":"string",
        "entrance_page":"string",
        "duration":"string",
        "site_id":"number",
        "site_domain_name":"string",
        "camapign_id":"number",
        "campaign_name":"string",
        "channel":"enum",
        "visitor_device":"enum",
        "visitor_id":"number",
        "visitor_country":"string",
        "visitor_city":"string",
        "visitor_region":"string",
        "visitor_ip_address":"string",
        "visitor_type":"enum",
        "visitor_browser_name":"string",
        "visitor_browser_version":"string",
        "visitor_os_name":"string",
        "visitor_os_version":"string",
        "visitor_provider":"string",
        "visitor_screen":"string",
        "visitor_language":"string",
        "visitor_custom_properties":[
          {
            "property_name":"string",
            "property_value":"string"
          }
        ],
        "utm_source":"string",
        "utm_medium":"string",
        "utm_term":"string",
        "utm_content":"string",
        "utm_campaign":"string",
        "openstat_ad":"string",
        "openstat_campaign":"string",
        "openstat_service":"string",
        "openstat_source":"string",
        "hits_count":"number",
        "hist":{
          "hit_time":"string",
          "hit_duration":"string",
          "hit_url":"string"
        },
        "segments":[
          {
            "segment_name":"string",
            "segment_id":"number"
          }
        ],
        "communications":[
          {
            "communication_type":"enum",
            "communication_id":"number",
            "communication_date_time":"iso8601"
          }
        ]
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "Список ошибок для методов с глаголом get"


## `ОТЛОЖЕН ДО ПОЛУЧЕНИЯ ЗАПРОСА ОТ КЛИЕНТОВ` Получение информации о посетителе

Поговорили с Юдаков Артём кесы его использования на текущий момент в ЛК в качестве проверки (тестовые цели и тестовые посетители) во время настроек РК

Метод | `get.visitors_report`
:---- | :---------------
Версия API | v2
Описание | Получение информации о посетителе
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"
`visitor_id` | number | да |  | Уникальный идентификатор посетителя

### Параметры ответа

<table>
	<tbody>
		<tr>
			<th>Название</th>
			<th>Тип</th>
			<th>Допустимые значения</th>
			<th>Фильтрация</th>
			<th>Сортировка</th>
			<th>Ответ по умолчанию</th>
			<th>Описание</th>
		</tr>
		<tr>
			<td><code>id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный идентификатор
посетителя</td>
		</tr>
		<tr>
			<td><code>first_visit</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD HH:MM:SS</td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>Дата и время первого посещения</td>
		</tr>
		<tr>
			<td><code>last_visit</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD HH:MM:SS</td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>Дата и время последнего посещения</td>
		</tr>
		<tr>
			<td><code>full_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td>да</td>
			<td>Фамилия Имя Отчество посетителя</td>
		</tr>
		<tr>
			<td><code>emails</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Адреса электронной почты
посетителя</td>
		</tr>
		<tr>
			<td><code>phone_numbers</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Номера телефонов посетителя</td>
		</tr>
		<tr>
			<td><code>company</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td></td>
			<td>Название компании посетителя</td>
		</tr>
		<tr>
			<td><code>person_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор персоны</td>
		</tr>
		<tr>
			<td><code>device</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>desktop</code></li>
					<li><code>mobile</code></li>
					<li><code>tablet</code></li>
					<li><code>other</code></li>
				</ul>
			</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Устройство посетителя</td>
		</tr>
		<tr>
			<td><code>visits_count</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Количество посещений</td>
		</tr>
		<tr>
			<td><code>comment</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Комментарий к посетителю</td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Уникальный идентификатор первой
				рекламной кампании. См. метод <code>"get.campaigns"</code>
			</td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Название первой рекламной кампании</td>
		</tr>
		<tr>
			<td><code>last_search_query</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Последний поисковый запрос</td>
		</tr>
		<tr>
			<td><code>first_search_query</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Первый поисковый запрос</td>
		</tr>
		<tr>
			<td><code>first_entrance_page</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Первая страница входа <blockquote><code>page_id</code> из первой сессии
посетителя</blockquote></td>
		</tr>
		<tr>
			<td><code>last_entrance_page</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Последняя страница входа <blockquote><code>page_id</code> из последней
сессии посетителя</blockquote></td>
		</tr>
		<tr>
			<td><code>last_session_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td>да</td>
			<td>Уникальный идентификатор
последней сессии посетителя</td>
		</tr>
		<tr>
			<td colspan="7">Обращения</td>
		</tr>
		<tr>
			<td><code>communications</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>Список всех обращений посетителя</td>
		</tr>
		<tr>
			<td><code>communication_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор
обращения</td>
		</tr>
		<tr>
			<td><code>communication_date_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td></td>
			<td></td>
			<td>Дата и время обращения</td>
		</tr>
		<tr>
			<td><code>communication_type</code></td>
			<td>enum</td>
			<td><code>call</code>, <code>chat</code>, <code>offline_message</code>, <code>goal</code></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Тип обращения</td>
		</tr>
		<tr>
			<td colspan="7">Дополнительные свойства посетителя</td>
		</tr>
		<tr>
			<td><code>custom_properties</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Свойства посетителя, которые могут
				быть заданы через личный кабинет
				или с помощью JavaScript API [метод
				<code>Comagic.setProperty(name, value);</code>]
			</td>
		</tr>
		<tr>
			<td><code>property_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название свойства посетителя</td>
		</tr>
		<tr>
			<td><code>property_value</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Значение свойства посетителя</td>
		</tr>
		<tr>
			<td colspan="7">Сайт</td>
		</tr>
		<tr>
			<td><code>site_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Уникальный идентификатор сайта</td>
		</tr>
		<tr>
			<td><code>site_domain_name</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Адрес сайта в интернете. Без указания
				протокола - <code>"http://"</code> или <code>"https://"</code>.
			</td>
		</tr>
		<tr>
			<td><code>site_duration</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Количество времени проведенных на
сайте, значение в секундах</td>
		</tr>
		<tr>
			<td colspan="7">Рекламные кампании</td>
		</tr>
		<tr>
			<td><code>campaigns</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Массив рекламных компаний по
				которым были заходы посетителя.
				См. метод <code>"get.campaigns"</code>
			</td>
		</tr>
		<tr>
			<td><code>campaign_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Уникальный идентификатор
рекламной кампании</td>
		</tr>
		<tr>
			<td><code>campaign_name</code></td>
			<td>string</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>Название рекламной кампании</td>
		</tr>
		<tr>
			<td colspan="7">Сессии посетителя</td>
		</tr>
		<tr>
			<td><code>sessions</code></td>
			<td>array</td>
			<td></td>
			<td>да</td>
			<td></td>
			<td></td>
			<td>
				Массив уникальных идентификаторов
				сессий посетителя, см. метод <code>"get.visitor_session_report"</code>
			</td>
		</tr>
		<tr>
			<td><code>session_id</code></td>
			<td>number</td>
			<td></td>
			<td></td>
			<td></td>
			<td></td>
			<td>
				Уникальный идентификатор сессии
посетителя
<blockquote>Сортировка по дате, от первой к последней</blockquote>
			</td>
		</tr>
	</tbody>
</table>


### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.visitors_report",
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
    "success":"true",
    "metadata":{

    },
    "data":[
      {
        "id":"number",
        "first_visit":"iso8601",
        "last_visit":"iso8601",
        "full_name":"string",
        "first_entrance_page":"string",
        "last_entrance_page":"string",
        "first_search_query":"string",
        "last_search_query":"string",
        "last_session_id":"number",
        "communications":[
          {
            "communication_id":"number",
            "communication_date_time":"iso8601",
            "communication_type":"enum"
          }
        ],
        "custom_properties":[
          {
            "property_name":"string",
            "property_value":"string"
          }
        ],
        "emails":[

        ],
        "phone_numbers":[

        ],
        "company":"string",
        "person_id":"number",
        "sessions":[

        ],
        "visits_count":"number",
        "comment":"string",
        "visitor_first_campaign_id":"number",
        "visitor_first_campaign_name":"string",
        "site_id":"number",
        "site_domain_name":"string",
        "site_duration":"number",
        "campaigns":[
          {
            "campaign_id":"number",
            "campaign_name":"string"
          }
        ]
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "Список ошибок для методов с глаголом get"


## Получение списка сделок

Метод | `get.sales_report`
:---- | :---------------
Версия API | v3
Статус | не реализован
Группа методов | Heavy
Описание | Получение списка сделок
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`customer_id` | number | нет |  | Уникальный идентификатор клиента <blockquote>Является обязательным для партнёра</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей. По умолчанию "100".
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать <code>"limit"</code> записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`field` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"

### Параметры ответа

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
			<td><code>id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор сделки, см. метод <code>"create.tag_sales"</code></td>
		</tr>
		<tr>
			<td><code>date_time</code></td>
			<td>string</td>
			<td>да</td>
			<td>YYYY-MM-DD HH:MM:SS</td>
			<td>Дата и время сделки</td>
		</tr>
		<tr>
			<td><code>days_before_sale</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Дней между обращением и последующей продажей</td>
		</tr>
		<tr>
			<td><code>communication_number</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Номер обращения. Расcчитывается в рамках персоны.</td>
		</tr>
		<tr>
			<td><code>transaction_value</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Сумма сделки</td>
		</tr>
		<tr>
			<td><code>comment</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Комментарий к сделке</td>
		</tr>
		<tr>
			<td><code>ua_client_id</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор в Universal Analytics</td>
		</tr>
		<tr>
			<td colspan="5">Проставленные теги</td>
		</tr>
		<tr>
			<td><code>tag</code></td>
			<td>array</td>
			<td>да</td>
			<td></td>
			<td>Теги, см. метод <code>"get.tags"</code></td>
		</tr>
		<tr>
			<td><code>tag_id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор тега</td>
		</tr>
		<tr>
			<td><code>tag_name</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Название тега</td>
		</tr>
		<tr>
			<td colspan="5">Сайт</td>
		</tr>
		<tr>
			<td><code>site</code></td>
			<td>object</td>
			<td>да</td>
			<td></td>
			<td>Сайт, см. метод <code>"get.sites"</code></td>
		</tr>
		<tr>
			<td><code>site_id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор сайта</td>
		</tr>
		<tr>
			<td><code>site_domain_name</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Адрес сайта в интернете. Без указания протокола - <code>"http://"</code> или <code>"https://"</code></td>
		</tr>
		<tr>
			<td colspan="5">Рекламная кампания</td>
		</tr>
		<tr>
			<td><code>campaign</code></td>
			<td>object</td>
			<td>да</td>
			<td></td>
			<td>Рекламная кампания, см. метод <code>"get.campaigns"</code></td>
		</tr>
		<tr>
			<td><code>campaign_id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор рекламной кампании</td>
		</tr>
		<tr>
			<td><code>campaign_name</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Название рекламной кампании</td>
		</tr>
		<tr>
			<td colspan="5">Информация о посетителе</td>
		</tr>
		<tr>
			<td><code>visitor</code></td>
			<td>object</td>
			<td>да</td>
			<td></td>
			<td>Информация посетителе, см. метод <code>"get.visitors"</code></td>
		</tr>
		<tr>
			<td><code>visitor_id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_name</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Имя, которое оставил посетитель при подаче заявки</td>
		</tr>
		<tr>
			<td><code>visitor_phone_number</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Номер телефона посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_email</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Адреса электронной почты посетителя</td>
		</tr>
		<tr>
			<td><code>person_id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор персоны</td>
		</tr>
		<tr>
			<td><code>visitor_type</code></td>
			<td>string</td>
			<td>да</td>
			<td>Новый,
Вернувшийся,
Не заполнен</td>
			<td>Тип посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_session_id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор сессии посетителя, см. <code>"get.visitor_session_report"</code></td>
		</tr>
		<tr>
			<td><code>visits_count</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Общее количество посещений посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор первой рекламной кампании. См.
метод <code>"get.campaigns"</code></td>
		</tr>
		<tr>
			<td><code>visitor_first_campaign_name</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Название первой рекламной кампании</td>
		</tr>
		<tr>
			<td><code>visitor_city</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Город посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_region</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Регион посетителя</td>
		</tr>
		<tr>
			<td><code>visitor_country</code></td>
			<td>string</td>
			<td>да</td>
			<td></td>
			<td>Страна посетителя</td>
		</tr>
		<tr>
			<td colspan="5">Обращение</td>
		</tr>
		<tr>
			<td><code>communication</code></td>
			<td>object</td>
			<td>да</td>
			<td></td>
			<td>
				Обращение. Детализированную информацию по обращению
				можно получить используя следующие методы <code>"get.communications_report "</code>, <code>"get.chats_report "</code>, <code>"get.goals_report "</code>, <code>"get.offline_messages_report "</code>, <code>"get.calls_report"</code>
			</td>
		</tr>
		<tr>
			<td><code>communication_id</code></td>
			<td>number</td>
			<td>да</td>
			<td></td>
			<td>Уникальный идентификатор обращения</td>
		</tr>
		<tr>
			<td><code>communication_type</code></td>
			<td>string</td>
			<td>да</td>
			<td>
				<code>chat</code>, <code>goal</code>, <code>call</code>,
				<code>offline_message</code>
			</td>
			<td>Тип обращения</td>
		</tr>
		<tr>
			<td><code>communication_date_time</code></td>
			<td>string</td>
			<td>да</td>
			<td>YYYY-MM-DD HH:MM:SS</td>
			<td>Дата и время обращения</td>
		</tr>
	</tbody>
</table>

### Параметры критериев фильтрации

Название параметра | Операторы фильтрации | Допустимые значения
:----------- | :-------- | :---
`date_from` | `eq` | YYYY-MM-DD HH:MM:SS или YYYY-MM-DD
`date_till` | `eq` | YYYY-MM-DD HH:MM:SS или YYYY-MM-DD
`id` | `eq`, `ne` | 
`site_id` | `eq`, `ne` | 
`site_domain_name` | `eq`, `ne`, `co` | 
`campaign_id` | `eq`, `ne` | 
`campaign_name` | `eq`, `ne`, `co` | 
`person_id` | `eq`, `ne` | 
`visitor_id` | `eq`, `ne` | 
`visitor_type` | `eq`, `ne` | 
`visitor_city` | `eq`, `ne`, `co` | 
`visitor_country` | `eq`, `ne`, `co` | 
`visitor_region` | `eq`, `ne`, `co` | 
`visitor_first_campaign_id` | `eq`, `ne` | 
`visitor_first_campaign_name` | `eq`, `ne`, `co` | 
`transaction_value` | `eq`, `ne`, `le`, `lt`, `gt`, `ge` | 
`days_before_sale` | `eq`, `ne`, `le`, `lt`, `gt`, `ge` | 
`visits_count` | `eq`, `ne`, `le`, `lt`, `gt`, `ge` | 
`communication_type` | `eq`, `ne` | 
`communication_id` | `eq`, `ne` | 

### Параметры сортировки данных

Название параметра |
--- |
`site_id` |
`campaign_id` |
`person_id` |
`days_before_sale` |
`communication_type` |
`visits_count` |
`transaction_value` |
`date_time` |

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.sales_report",
  "params":{
    "access_token":"string",
    "customer_id":"number",
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
    "field":[
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
    "meta_data":{

    },
    "data":[
      {
        "id":"number",
        "date_time":"string",
        "transaction_value":"number",
        "comment":"string",
        "days_before_sale":"number",
        "communication_number":"number",
        "ua_client_id":"string",
        "communication":{
          "communication_id":"number",
          "communication_type":"string",
          "communication_date_time":"string"
        },
        "tag":[
          {
            "tag_id":"number",
            "tag_name":"string"
          }
        ],
        "site":{
          "site_id":"number",
          "site_domain_name":"string"
        },
        "campaign":{
          "campaign_id":"number",
          "campaign_name":"string",
          "visit_other_campaign":"boolean"
        },
        "visitor":{
          "visitor_id":"number",
          "visitor_name":"string",
          "visitor_phone_number":"number",
          "visitor_email":"string",
          "person_id":"number",
          "visitor_type":"string",
          "visitor_session_id":"number",
          "visits_count":"number",
          "visitor_first_campaign_id":"number",
          "visitor_first_campaign_name":"string",
          "visitor_city":"string",
          "visitor_region":"string",
          "visitor_country":"string"
        }
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Текст ошибки | Код ошибки | Мнемокод ошибки
:----------- | :-------- | :--
 |  | 


## Получение общего отчёта истории списаний по дням

Метод | `get.financial_summary_report`
:---- | :---------------
Версия API | v2
Описание | Получение общего отчёта истории списаний по дням
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"
`year` | number | да | YYYY | Год за который будут доступны начисления <blockquote>За любой год, с которого у нас клиент. Если функция возвращает пустоту, это ок</blockquote>
`month` | number | да | <ul><li>1 - Январь</li> <li>2 - Февраль </li><li>3 - Март </li><li>4 - Апрель </li><li>5 - Май </li><li>6 - Июнь </li><li>7 - Июль </li><li>8 - Август </li><li>9 - Сентябрь </li><li>10 - Октябрь </li><li>11 - Ноябрь </li><li>12 - Декабрь</li></ul> | Месяц, за который будут доступны начисления <blockquote>За любой месяц, с которого у нас клиент. Если функция возвращает пустоту, это ок</blockquote>

### Параметры ответа

Название | Тип  | Допустимые значения | Описание
:------- | :--- | :------------------ | :-------
`date` | iso8601 | YYYY-MM-DD | Дата списания
`total_charge` | number |  | Всего списано со счета
`bonuses_charge` | number |  | Оплачено бонусами
`subscriber_fee` | number |  | Абонентская плата
`telecom_services` | number |  | Услуги связи
`additional_services` | number |  | Дополнительные услуги
`one_off_services` | number |  | Разовые усоуги
`changes` | number |  | Корректировки

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.financial_summary_report",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "offset":"number",
    "limit":"number",
    "year":"number",
    "month":"number",
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
        "date":"iso8601",
        "total_charge":"number",
        "bonuses_charge":"number",
        "subscriber_fee":"number",
        "telecom_services":"number",
        "additional_services":"number",
        "one_off_services":"number",
        "changes":"number"
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "Список ошибок для методов с глаголом get"


## `ДОСТУПНО КЛИЕНТАМ` Получение детализированного отчёта истории списаний по всем
плечам звонковых сессий

Метод | `get.financial_call_legs_report`
:---- | :---------------
Версия API | v2
Описание | Получение детализированного отчёта истории списаний по всем плечам звонковых сессий
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

> Звонки с форм консультанта и сайтфона считаются исходящими звонками.

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`user_id` | number | нет |  | Уникальный идентификатор пользователя клиента агента от имени которого делается запрос <blockquote>Является обязательным для агента</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей.
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`fields` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"
`date_from` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата начала выборки
`date_till` | iso8601 | да | YYYY-MM-DD hh:mm:ss | Дата окончания выборки

### Параметры ответа

<table>
	<tbody>
		<tr>
			<th>Название</th>
			<th>Тип</th>
			<th>Допустимые значения</th>
			<th>Фильтрация</th>
			<th>Сортировка</th>
			<th>Ответ по умолчанию</th>
			<th>Описание</th>
		</tr>
		<tr>
			<td><code>start_time</code></td>
			<td>iso8601</td>
			<td>YYYY-MM-DD hh:mm:ss</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>Дата и время плеча</td>
		</tr>
		<tr>
			<td><code>direction</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>in</code> - Входящие;</li>
					<li><code>out</code> - Исходящие</li>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Направление плеча</td>
		</tr>
		<tr>
			<td><code>source</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>callapi</code> - Call API;</li>
					<li><code>callapi_informer_call</code> - Call API информационный звонок;</li>
					<li><code>callapi_scenario_call</code> - Call API вызов сценария</li>
					<li><code>callback</code> - Callback;</li>
					<li><code>callout</code> - Callout;</li>
					<li><code>call_tracking</code>- Аналитика;</li>
					<li><code>dynamic_call_tracking</code> - Динамический коллтрекинг;</li>
					<li><code>va</code> - Виртуальная АТС;</li>
					<li><code>sip</code> - Исходящий с SIP;</li>
					<li><code>consultant</code> - Звонок через Консультант;</li>
					<li><code>lead</code> - Звонок через Лидогенератор;</li>
					<li><code>sitephone</code> - Звонок через Сайтфон;</li>
					<li><code>faxout</code> - Исходящий факс;</li>
					<li><code>retailcrm</code> - retailCRM</li>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Источник плеча</td>
		</tr>
		<tr>
			<td><code>call_session_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>
				Уникальный
				идентификатор сессии
				звонка, см. метод <code>"get.calls_report"</code>
			</td>
		</tr>
		<tr>
			<td><code>leg_id</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>
				Уникальный
				идентификатор звонка,
				см. метод <code>"get.call_legs_report"</code> <blockquote>В рамках одной
				сессии звонка
				возможно
				несколько
				вызовов</blockquote>
			</td>
		</tr>
		<tr>
			<td><code>calling_phone_number</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Номер телефона звонящего</td>
		</tr>
		<tr>
			<td><code>called_phone_number</code></td>
			<td>string</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Номер телефона на который звонили</td>
		</tr>
		<tr>
			<td><code>duration</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Продолжительность звонка, значение в секундах</td>
		</tr>
		<tr>
			<td><code>chargeable_duration</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Тарифицированная длительность звонка, значение в секундах</td>
		</tr>
		<tr>
			<td><code>direction_type</code></td>
			<td>enum</td>
			<td>
				<ul>
					<li><code>international</code> - Международные;</li>
					<li><code>national</code> - Междугородние;</li>
					<li><code>local</code> - Местные (Москва и Московская область);</li>
					<li><code>mobile</code> - Мобильные</li>
				</ul>
			</td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Тип направления звонка</td>
		</tr>
		<tr>
			<td><code>cost_per_minute</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Стоимость за минуту</td>
		</tr>
		<tr>
			<td><code>total_charge</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Общая стоимость звонка</td>
		</tr>
		<tr>
			<td><code>bonuses_charge</code></td>
			<td>number</td>
			<td></td>
			<td>да</td>
			<td>да</td>
			<td>да</td>
			<td>Оплачено бонусами</td>
		</tr>
	</tbody>
</table>
 

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.financial_call_legs_report",
  "params":{
    "access_token":"string",
    "user_id":"number",
    "offset":"number",
    "limit":"number",
    "date_from":"iso8601",
    "date_till":"iso8601",
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
        "start_time":"iso8601",
        "direction":"enum",
        "source":"enum",
        "call_session_id":"string",
        "leg_id":"number",
        "calling_phone_number":"string",
        "called_phone_number":"string",
        "duration":"number",
        "chargeable_duration":"number",
        "direction_type":"enum",
        "cost_per_minute":"number",
        "total_charge":"number",
        "bonuses_charge":"number"
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Смотрим раздел "Список ошибок для методов с глаголом get"


## Получение отчёт по запросам к любому виду API

Метод | `get.api_requests_report`
:---- | :---------------
Версия API | v3
Статус | не реализован
Группа методов | Heavy
Описание | Получение отчёта по запросам к любому виду API
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`customer_id` | number | нет |  | Уникальный идентификатор клиента <blockquote>Является обязательным для партнёра</blockquote>
`limit` | number | нет |  | Количество возвращаемых записей. По умолчанию "100".
`offset` | number | нет |  | Сдвиг, определяет с какого номера записи возвращать `"limit"` записей. По умолчанию "0".
`filter` | object | нет |  | См. раздел "Критерии фильтрации"
`field` | array | нет |  | См. раздел "Представление возвращаемых данных"
`sort` | array | нет |  | См. раздел "Сортировка данных"

### Параметры ответа

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`date_time` | string | да | YYYY-MM-DD HH:MM:SS | Дата и время запроса
`request_id` | number | да |  | Уникальный идентификатор запроса согласно спецификации JSON RPC 2.0 (`"id"`)
`type` | string | да | `call_api`, `rpc_api` | Тип API
`component` | string | да | Возможные значения указаны в разделе "Биллинг" (см. Data API v2.x и Technical Specification: Call API v4.0) | Название компонента
`ip_address` | string | да |  | IP адрес с которого делался запрос
`method` | string | да |  | Название метода
`method_type` | string | да | `heavy`, `light`, `medium` | Тип метода
`result` | string | да | <ul><li>`success` - Запрос успешно выполнен;</li><li>`error` - Запрос завершился ошибкой</li></ul> | Результат выполнения запроса
`error_code` | string | да |  | Код ошибки
`error_mnemocode` | string | да |  | Мнемокод ошибки
`call_session_id` | string | да |  | Уникальный идентификатор сессии вызова через Call API, см. метод `"get.calls_report"`
`external_id` | string | да |  | Уникальный идентификатор запроса к Call API во внешней системе
`raw` | string | да |  | Исходный запрос
`execution_time` | number | да |  | Время выполнения запроса, значение в миллисекундах

### Параметры критериев фильтрации

Название параметра | Операторы фильтрации | Допустимые значения
:----------- | :-------- | :---
`date_from` | `eq` | YYYY-MM-DD HH:MM:SS или YYYY-MM-DD
`date_till` | `eq` | YYYY-MM-DD HH:MM:SS или YYYY-MM-DD
`call_session_id` | `eq`, `ne` | 
`type` | `eq`, `ne` | 
`request_id` | `eq`, `ne` | 
`ip_address` | `eq`, `ne`, `sw`, `ew`, `co` | 
`result` | `eq`, `ne` | 
`method` | `eq`, `ne`, `co` | 
`error_mnemocode` | `eq`, `ne` | 
`external_id` | `eq`, `ne` | 

### Параметры сортировки данных

Название параметра | 
--- |
`date_time` |
`type` |
`ip_address` |
`result` |
`method` |
`error_mnemocode` |
`external_id` |
`method_type` |
`component` |

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"get.api_requests_report",
  "params":{
    "access_token":"string",
    "customer_id":"number",
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
    "field":[
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
        "date_time":"string",
        "request_id":"number",
        "type":"string",
        "component":"string",
        "ip_address":"string",
        "method":"string",
        "method_type":"string",
        "result":"string",
        "error_code":"string",
        "error_mnemocode":"string",
        "call_session_id":"string",
        "external_id":"string",
        "raw":"string",
        "execution_time":"number"
      }
    ]
  }
}
```

### Список возвращаемых ошибок

Текст ошибки | Код ошибки | Мнемокод ошибки
:----------- | :-------- | :--
 |  | 


## Присвоение `visitor_id` обращению звонок

Метод | `set.visitor_communication`
:---- | :---------------
Версия API | v2
Описание | Присвоение `visitor_id` обращению в рамках сайта
Кому доступен | Партнёр, Клиент
Ссылка | Вернуться к списку методов

### Параметры запроса

Название | Тип  | Обязательный | Допустимые значения | Описание
:------- | :--- | :----------: | :------------------ | :-------
`access_token` | string | да |  | Ключ сессии аутентификации
`customer_id` | number | нет |  | Уникальный идентификатор клиента <blockquote>Является обязательным для партнёра</blockquote>
`communication_id` | number | да |  | Уникальный идентификатор обращения. По данному идентификатору можно получить детализированную информацию используя следующие методы `"get.communications_report"`, `"get.chats_report "`, `"get.goals_report "`, `"get.offline_messages_report "`, `"get.calls_report"`
`cummunication_type` | string | да | `chat`, `call`, `goal`, `offline_message` | Уникальный идентификатор обращения. По данному идентификатору можно получить детализированную информацию используя следующие методы `"get.communications_report "`, `"get.chats_report "`, `"get.goals_report "`, `"get.offline_messages_report "`, `"get.calls_report"`
`visitor_id` | number | да |  | Уникальный идентификатор тега, см. метод `"get.visitors"`

### JSON структура запроса

```json
{
  "jsonrpc":"2.0",
  "id":"number",
  "method":"set.visitor_communication",
  "params":{
    "access_token":"string",
    "customer_id":"number",
    "communication_id":"number",
    "communication_type":"string",
    "visitor_id":"number"
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

Текст ошибки | Код ошибки | Мнемокод ошибки
:----------- | :-------- | :--
 |  | 