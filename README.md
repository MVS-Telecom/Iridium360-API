# Iridium360-API

![image](https://user-images.githubusercontent.com/11313401/114893018-f2cdaf80-9e15-11eb-8f29-5a30734c0c04.png)

В данном репозитории представлено описание работы с HTTP API портала [iridium360.ru](https://iridium360.ru)

Вы можете использовать это API для интеграции портала iridium360.ru в ваш сервис, сайт или приложение

> **Для работы с API вам необходимо получить токен** в настройках вашего аккаунта на портале iridium360.ru


# Получение токена
1. [Войдите](https://www.iridium360.ru/workplace/device) в личный кабинет iridium360.ru
2. Перейдите на страницу [настроек аккаунта](https://www.iridium360.ru/Workplace/preferences)
3. В разделе `API` включите **Разрешить API**
4. Нажмите кнопку **Получить новый токен API**

<img width="678" alt="Screenshot 2021-04-15 at 18 28 14" src="https://user-images.githubusercontent.com/11313401/114896063-ae8fde80-9e18-11eb-855d-37a8b62d4c82.png">


# Описание API

> Проверить работу API прямо из браузера можно по ссылке [Swagger UI](https://service.iridium360.ru/swagger/index.html)

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/account`

*Получить информацию об аккаунте*

<h3 id="get__rockstar-public_api_v1_account-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|service-session|header|string|true|API токен|


<h3 id="get__rockstar-public_api_v1_account-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|array [[ApiAccountView](#schemaapiaccountview)]|

> Пример ответа

```json
{
  "username": "Иван Иванов",
  "email": "example@mail.ru",
  "phone": "+79153925491",
  "avatar": "https://www.iridium360.ru/api/images/raw/270b62759cf0438aacbd0304503225e0/209c61991f9c4af682d034442f746b12_M"
}
```

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/points`

*Получить список точек устройства*

<h3 id="get__rockstar-public_api_v1_points-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|deviceSerial|query|string|true|Серийный номер устройства|
|start|query|string(date-time)|false|Дата (вкл) с которой выдать точки|
|end|query|string(date-time)|false|Дата (вкл) до которой выдать точки|
|count|query|integer(int32)|false|Максимальное кол-во выдаваемых точек|
|service-session|header|string|true|API токен|


<h3 id="get__rockstar-public_api_v1_points-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|array [[ApiDevicePointView](#schemaapidevicepointview)]|

> Пример ответа

```json
[
  {
    "id": "w7oUijvyIECNJPl2pFNnzg",
    "location": {
      "lat": -19.858583,
      "lon": 141.005343,
      "date": "2021-01-25T14:15:22Z",
      "alt": 2
    }
  },
  {
    "id": "YEAJoY2FdUiSN8itgj3d3Q",
    "location": {
      "lat": -19.85858,
      "lon": 141.00531,
      "date": "2021-01-24T08:01:54Z",
      "alt": 3
    }
  },
  {
    "id": "W0LBoaFjKkCiSavE8ehTPQ",
    "location": {
      "lat": -19.85855,
      "lon": 141.00529,
      "date": "2021-01-24T04:32:19Z",
      "alt": 2
    }
  }
]
```

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/points/{id}`

*Получить инфу о точке устройства*

<h3 id="get__rockstar-public_api_v1_points_{id}-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|id|path|string|true|Id точки|
|service-session|header|string|true|API токен|


<h3 id="get__rockstar-public_api_v1_points_{id}-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiDevicePointView](#schemaapidevicepointview)|

> Пример ответа

```json
{
    "id": "YEAJoY2FdUiSN8itgj3d3Q",
    "location": {
      "lat": -19.85858,
      "lon": 141.00531,
      "date": "2021-01-24T08:01:54Z",
      "alt": 3
    }
  }
```

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/devices`

*Получить устройства в аккаунте*

<h3 id="get__rockstar-public_api_v1_devices-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|service-session|header|string|true|API токен|


<h3 id="get__rockstar-public_api_v1_devices-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|array [[ApiDeviceView](#schemaapideviceview)]|

> Пример ответа

```json
[
  {
    "time": "2021-01-24T14:15:22Z",
    "serialNumber": "10976",
    "imei": "1088310395832939554821",
    "lastLocation": {
      "lat": -19.85858,
      "lon": 141.00531,
      "date": "2021-01-23T08:01:54Z",
      "alt": 3
    }
  },
  {
    "time": "2021-01-24T14:15:22Z",
    "serialNumber": "209356",
    "imei": "1088310383288683021",
    "lastLocation": {
      "lat": -42.792091,
      "lon": 146.909608,
      "date": "2021-01-23T08:01:54Z",
      "alt": 12
    }
  },
  {
    "time": "2021-01-24T14:15:22Z",
    "serialNumber": "509382",
    "imei": "1049284103856105938",
    "lastLocation": {
      "lat": -39.327232,
      "lon": 175.659989,
      "date": "2021-01-23T02:12:28Z",
      "alt": 9
    }
  }
]
```

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/devices/{id}`

*Получить устройство по серийному номеру в аккаунте*

<h3 id="get__rockstar-public_api_v1_devices_{id}-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|id|path|string|true|Серийный номер устройства|
|service-session|header|string|true|API токен|


<h3 id="get__rockstar-public_api_v1_devices_{id}-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiDeviceView](#schemaapideviceview)|


> Пример ответа

```json
{
    "time": "2021-01-24T14:15:22Z",
    "serialNumber": "209356",
    "imei": "1088310383288683021",
    "lastLocation": {
      "lat": -42.792091,
      "lon": 146.909608,
      "date": "2021-01-23T08:01:54Z",
      "alt": 12
    }
  }
```

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/messages`

*Получить сообщения отправленные / полученные с устройства*

<h3 id="get__rockstar-public_api_v1_messages-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|deviceSerial|query|string|true|Серийный номер устройства|
|startId|query|string|false|Id сообщения (включительно), с которого нужно выдать сообщения|
|count|query|integer(int32)|false|Кол-во сообщений|
|service-session|header|string|true|API токен|


<h3 id="get__rockstar-public_api_v1_messages-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|array [[ApiMessageView](#schemaapimessageview)]|

> Пример ответа

```json
[
  {
    "id": "oyYFZZaGDUmt3R7iUItuyg",
    "date": "2021-01-24T14:15:22Z",
    "text": "сообщение с устройства на портал",
    "direction": "FromDevice",
    "location": {
      "lat": -19.858583,
      "lon": 141.005343,
      "date": "2021-01-24T14:13:15Z",
      "alt": 2
    }
  },
  {
    "id": "yacgLXd4sUGJaNiZmdfhAQ",
    "date": "2021-01-24T14:15:22Z",
    "text": "сообщение с устройства на мобильный",
    "direction": "FromDevice",
    "location": {
      "lat": -19.858583,
      "lon": 141.005343,
      "date": "2021-01-24T14:13:15Z",
      "alt": 2
    },
    "childs": [
      {
        "id": "gnbX6EfGX0SSQavaUkhUkA",
        "date": "2021-01-24T14:15:22Z",
        "text": "сообщение с устройства на мобильный",
        "direction": "FromDevice",
        "subscriber": "79153925491",
        "location": {
          "lat": -19.858583,
          "lon": 141.005343,
          "date": "2021-01-24T14:13:15Z",
          "alt": 2
        }
      }
    ]
  },
]
```

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/messages/{id}`

*Получить сообщение по id, а также его дочерние сообщения (при их наличии)*

<h3 id="get__rockstar-public_api_v1_messages_{id}-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|id|path|string|true|Id сообщения|
|service-session|header|string|true|API токен|


<h3 id="get__rockstar-public_api_v1_messages_{id}-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiMessageView](#schemaapimessageview)|

> Пример ответа

```json
{
    "id": "yacgLXd4sUGJaNiZmdfhAQ",
    "date": "2021-01-24T14:15:22Z",
    "text": "сообщение с устройства на мобильный",
    "direction": "FromDevice",
    "location": {
      "lat": -19.858583,
      "lon": 141.005343,
      "date": "2021-01-24T14:13:15Z",
      "alt": 2
    },
    "childs": [
      {
        "id": "gnbX6EfGX0SSQavaUkhUkA",
        "date": "2021-01-24T14:15:22Z",
        "text": "сообщение с устройства на мобильный",
        "direction": "FromDevice",
        "subscriber": "79153925491",
        "location": {
          "lat": -19.858583,
          "lon": 141.005343,
          "date": "2021-01-24T14:13:15Z",
          "alt": 2
        }
      }
    ]
}
```

***
`POST https://service.iridium360.ru/rockstar-public/api/v1/messages/send`

*Отправить сообщение на устройство*

<h3 id="post__rockstar-public_api_v1_messages_send-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|deviceSerial|query|string|true|Серийный номер устройства|
|useMobileNumber|query|boolean|false|Использовать мобильный номер аккаунта в качестве отправителя сообщения. По умолчанию используется email аккаунта|
|service-session|header|string|true|API токен|
|messageText|body|string|true|Текст сообщения|

<h3 id="post__rockstar-public_api_v1_messages_send-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiMessageView](#schemaapimessageview)|

> Пример ответа

```json
{
  "id": "VzOZYD0KNUWZ6TxDqHqFpw",
  "date": "2021-01-26T14:15:22Z",
  "text": "привет! как дела?",
  "direction": "ToDevice",
  "subscriber": "79153925491"
}
```

# Структуры

<h2 id="tocS_ApiAccountView">ApiAccountView</h2>

*Структура, содержащая информацию об аккаунте*
<!-- backwards compatibility -->
<a id="schemaapiaccountview"></a>
<a id="schema_ApiAccountView"></a>
<a id="tocSapiaccountview"></a>
<a id="tocsapiaccountview"></a>

```json
{
  "username": "string",
  "email": "string",
  "phone": "string",
  "avatar": "string"
}

```

### Параметры

|Имя|Тип|Обязательно|Ограничения|Описание|
|---|---|---|---|---|
|username|string¦null|true|none|Имя пользователя|
|email|string¦null|true|none|Email|
|phone|string¦null|false|none|Номер мобильного телефона|
|avatar|string¦null|false|none|Ссылка на аватар|

<h2 id="tocS_ApiDevicePointView">ApiDevicePointView</h2>

*Структура, содержащая информацию о точке устройства*
<!-- backwards compatibility -->
<a id="schemaapidevicepointview"></a>
<a id="schema_ApiDevicePointView"></a>
<a id="tocSapidevicepointview"></a>
<a id="tocsapidevicepointview"></a>

```json
{
  "id": "string",
  "location": {
    "lat": 0,
    "lon": 0,
    "date": "2019-08-24T14:15:22Z",
    "alt": 0
  }
}

```

### Параметры

|Имя|Тип|Обязательно|Ограничения|Описание|
|---|---|---|---|---|
|id|string¦null|true|none|Id точки|
|location|[Location](#schemalocation)|true|none|Координаты точки|

<h2 id="tocS_ApiDeviceView">ApiDeviceView</h2>

*Структура, содержащая информацию об устройстве*
<!-- backwards compatibility -->
<a id="schemaapideviceview"></a>
<a id="schema_ApiDeviceView"></a>
<a id="tocSapideviceview"></a>
<a id="tocsapideviceview"></a>

```json
{
  "time": "2019-08-24T14:15:22Z",
  "serialNumber": "string",
  "imei": "string",
  "lastLocation": {
    "lat": 0,
    "lon": 0,
    "date": "2019-08-24T14:15:22Z",
    "alt": 0
  }
}

```

### Параметры

|Имя|Тип|Обязательно|Ограничения|Описание|
|---|---|---|---|---|
|time|string(date-time)¦null|true|none|Дата актуальности данных|
|serialNumber|string¦null|true|none|Серийный номер устройства|
|imei|string¦null|true|none|IMEI устройства|
|lastLocation|[Location](#schemalocation)|false|none|Последнее известное местоположение устройства|

<h2 id="tocS_ApiMessageView">ApiMessageView</h2>

*Структура, содержащая информацию о сообщении*
<!-- backwards compatibility -->
<a id="schemaapimessageview"></a>
<a id="schema_ApiMessageView"></a>
<a id="tocSapimessageview"></a>
<a id="tocsapimessageview"></a>

```json
{
  "id": "string",
  "date": "2019-08-24T14:15:22Z",
  "text": "string",
  "direction": "FromDevice",
  "subscriber": "string",
  "location": {
    "lat": 0,
    "lon": 0,
    "date": "2019-08-24T14:15:22Z",
    "alt": 0
  },
  "childs": []
}

```

### Параметры

|Имя|Тип|Обязательно|Ограничения|Описание|
|---|---|---|---|---|
|id|string¦null|true|none|Id сообщения|
|date|string(date-time)|true|none|Дата получения / отправки|
|text|string¦null|true|none|Текст сообщения|
|direction|[MessageDirection](#schemamessagedirection)|true|none|Направление сообщения|
|subscriber|string¦null|false|none|Отправитель / получатель|
|location|[Location](#schemalocation)|true|none|Координаты отправки сообщения|
|childs|array [[ApiMessageView](#schemaapimessageview)]¦null|false|none|Дочерние сообщения*|

> *Одно сообщение, отправленное с устройства может быть доставлено нескольким получателям (например, на мобильный телефон и email) в завимости от настроек в личном кабинете

<h2 id="tocS_Location">Location</h2>

*Структура, содержащая координаты*
<!-- backwards compatibility -->
<a id="schemalocation"></a>
<a id="schema_Location"></a>
<a id="tocSlocation"></a>
<a id="tocslocation"></a>

```json
{
  "lat": 0,
  "lon": 0,
  "date": "2019-08-24T14:15:22Z",
  "alt": 0
}

```

### Параметры

|Имя|Тип|Обязательно|Ограничения|Описание|
|---|---|---|---|---|
|lat|number(double)|true|none|Широта|
|lon|number(double)|true|none|Долгота|
|date|string(date-time)¦null|true|none|Дата|
|alt|number(double)¦null|false|none|Высота|

<h2 id="tocS_MessageDirection">MessageDirection</h2>

*Направление сообщения*
<!-- backwards compatibility -->
<a id="schemamessagedirection"></a>
<a id="schema_MessageDirection"></a>
<a id="tocSmessagedirection"></a>
<a id="tocsmessagedirection"></a>


#### Значения

|Значение|Описание|
|---|---|
|FromDevice|Сообщение с устройства|
|ToDevice|Сообщение на устройство|




