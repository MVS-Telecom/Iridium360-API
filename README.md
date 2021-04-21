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


> 200 HTTP

```json
{
  "username": "string",
  "email": "string",
  "phone": "string",
  "avatar": "string"
}
```

<h3 id="get__rockstar-public_api_v1_account-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiAccountView](#schemaapiaccountview)|

<aside class="success">

</aside>

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/points`

*Получить список точек устройства*

<h3 id="get__rockstar-public_api_v1_points-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|deviceSerial|query|string|false|Серийный номер устройства|
|start|query|string(date-time)|false|Дата (вкл) с которой выдать точки|
|end|query|string(date-time)|false|Дата (вкл) до которой выдать точки|
|count|query|integer(int32)|false|Максимальное кол-во выдаваемых точек|
|service-session|header|string|true|API токен|

> 200 HTTP

```json
[
  {
    "id": "string",
    "location": {
      "lat": 0,
      "lon": 0,
      "date": "2019-08-24T14:15:22Z",
      "alt": 0
    }
  }
]
```

<h3 id="get__rockstar-public_api_v1_points-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|

<h3 id="get__rockstar-public_api_v1_points-responseschema">Формат ответа</h3>

Status Code **200**

|Имя|Тип|Обязательно|Ограничения|Описание|
|---|---|---|---|---|
|*anonymous*|[[ApiDevicePointView](#schemaapidevicepointview)]|false|none|none|
|» id|string¦null|false|none|none|
|» location|[Location](#schemalocation)|false|none|none|
|»» lat|number(double)|false|none|none|
|»» lon|number(double)|false|none|none|
|»» date|string(date-time)¦null|false|none|none|
|»» alt|number(double)¦null|false|none|none|

<aside class="success">

</aside>

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/points/{id}`

*Получить инфу о точке устройства*

<h3 id="get__rockstar-public_api_v1_points_{id}-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|id|path|string|true|Id точки|
|service-session|header|string|true|API токен|



> 200 HTTP

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

<h3 id="get__rockstar-public_api_v1_points_{id}-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiDevicePointView](#schemaapidevicepointview)|

<aside class="success">

</aside>

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/devices`

*Получить устройства в аккаунте*

<h3 id="get__rockstar-public_api_v1_devices-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|service-session|header|string|true|API токен|



> 200 HTTP

```json
[
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
]
```

<h3 id="get__rockstar-public_api_v1_devices-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|

<h3 id="get__rockstar-public_api_v1_devices-responseschema">Формат ответа</h3>

Status Code **200**

|Имя|Тип|Обязательно|Ограничения|Описание|
|---|---|---|---|---|
|*anonymous*|[[ApiDeviceView](#schemaapideviceview)]|false|none|none|
|» time|string(date-time)¦null|false|none|none|
|» serialNumber|string¦null|false|none|none|
|» imei|string¦null|false|none|none|
|» lastLocation|[Location](#schemalocation)|false|none|none|
|»» lat|number(double)|false|none|none|
|»» lon|number(double)|false|none|none|
|»» date|string(date-time)¦null|false|none|none|
|»» alt|number(double)¦null|false|none|none|

<aside class="success">

</aside>

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/devices/{id}`

*Получить устройство по серийному номеру в аккаунте*

<h3 id="get__rockstar-public_api_v1_devices_{id}-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|id|path|string|true|Серийный номер устройства|
|service-session|header|string|true|API токен|



> 200 HTTP

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

<h3 id="get__rockstar-public_api_v1_devices_{id}-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiDeviceView](#schemaapideviceview)|

<aside class="success">

</aside>

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/messages`

*Получить сообщения отправленные / полученные с устройства*

<h3 id="get__rockstar-public_api_v1_messages-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|deviceSerial|query|string|false|Серийник устройства|
|startId|query|string|false|Id сообщения (включительно), с которого нужно выдать сообщения|
|count|query|integer(int32)|false|Кол-во сообщений|
|service-session|header|string|true|API токен|



> 200 HTTP

```json
[
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
    }
  }
]
```

<h3 id="get__rockstar-public_api_v1_messages-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|

<h3 id="get__rockstar-public_api_v1_messages-responseschema">Формат ответа</h3>



|Имя|Тип|Обязательно|Ограничения|Описание|
|---|---|---|---|---|
|*anonymous*|[[ApiMessageView](#schemaapimessageview)]|false|none|none|
|» id|string¦null|false|none|none|
|» date|string(date-time)|false|none|none|
|» text|string¦null|false|none|none|
|» direction|[MessageDirection](#schemamessagedirection)|false|none|none|
|» subscriber|string¦null|false|none|none|
|» location|[Location](#schemalocation)|false|none|none|
|»» lat|number(double)|false|none|none|
|»» lon|number(double)|false|none|none|
|»» date|string(date-time)¦null|false|none|none|
|»» alt|number(double)¦null|false|none|none|

#### Значения

|Property|Value|
|---|---|
|direction|FromDevice|
|direction|ToDevice|

<aside class="success">

</aside>

***
`GET https://service.iridium360.ru/rockstar-public/api/v1/messages/{id}`

*Получить сообщение по id, а также его дочерние*** сообщения (при их наличии)*

<h3 id="get__rockstar-public_api_v1_messages_{id}-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|id|path|string|true|Id сообщения|
|service-session|header|string|true|API токен|



> 200 HTTP

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
  }
}
```

<h3 id="get__rockstar-public_api_v1_messages_{id}-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiMessageView](#schemaapimessageview)|

<aside class="success">

</aside>

***
`POST https://service.iridium360.ru/rockstar-public/api/v1/messages/send`

*Отправить сообщение на устройство*

<h3 id="post__rockstar-public_api_v1_messages_send-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательно|Описание|
|---|---|---|---|---|
|deviceSerial|query|string|false|Серийный номер устройства|
|useMobileNumber|query|boolean|false|Использовать мобильный номер аккаунта в качестве отправителя сообщения. По умолчанию используется email аккаунта|
|service-session|header|string|true|API токен|
|body|body|string|false|Текст сообщения|



> 200 HTTP

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
  }
}
```

<h3 id="post__rockstar-public_api_v1_messages_send-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiMessageView](#schemaapimessageview)|

<aside class="success">

</aside>

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
|username|string¦null|false|none|Имя пользователя|
|email|string¦null|false|none|Email|
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
|id|string¦null|false|none|Id точки|
|location|[Location](#schemalocation)|false|none|Координаты точки|

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
|time|string(date-time)¦null|false|none|Дата актуальности данных|
|serialNumber|string¦null|false|none|Серийный номер устройства|
|imei|string¦null|false|none|IMEI устройства|
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
|id|string¦null|false|none|Id сообщения|
|date|string(date-time)|false|none|Дата получения / отправки|
|text|string¦null|false|none|Текст сообщения|
|direction|[MessageDirection](#schemamessagedirection)|false|none|Направление сообщения|
|subscriber|string¦null|false|none|Отправитель / получатель|
|location|[Location](#schemalocation)|false|none|Координаты отправки сообщения|
|childs|[[ApiMessageView](#schemaapimessageview)]¦null|false|none|Дочерние сообщения*|

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
|lat|number(double)|false|none|Широта|
|lon|number(double)|false|none|Долгота|
|date|string(date-time)¦null|false|none|Дата|
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




