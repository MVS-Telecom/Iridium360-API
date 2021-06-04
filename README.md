# Iridium360-API

![image](https://user-images.githubusercontent.com/11313401/114893018-f2cdaf80-9e15-11eb-8f29-5a30734c0c04.png)

В данном репозитории представлено описание работы с HTTP API портала [iridium360.ru](https://iridium360.ru)

Вы можете использовать этот API для интеграции портала iridium360.ru в ваш сервис, сайт или приложение

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
## Получить информацию об аккаунте

`GET https://service.iridium360.ru/rockstar-public/api/v1/account`

<h3 id="get__rockstar-public_api_v1_account-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательный|Описание|
|---|---|---|---|---|
|service-session|header|string|да|API токен|


<h3 id="get__rockstar-public_api_v1_account-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|array [[ApiAccountView](#apiaccountview)]|

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
## Получить устройства в аккаунте

`GET https://service.iridium360.ru/rockstar-public/api/v1/devices`

<h3 id="get__rockstar-public_api_v1_devices-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательный|Описание|
|---|---|---|---|---|
|service-session|header|string|да|API токен|


<h3 id="get__rockstar-public_api_v1_devices-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|array [[ApiDeviceView](#apideviceview)]|

> Пример ответа

```json
[
  {
    "id": "02IaVXbMpE6I06TgG5sWFA",
    "time": "2021-01-24T14:15:22Z",
    "serialNumber": "10976",
    "imei": "1088310395832939554821",
    "lastLocation": {
      "lat": -19.85858,
      "lon": 141.00531,
      "date": "2021-01-23T08:01:54Z",
      "alt": 3
    },
    "owner" : {
      "email": "example@email.com",
    },
    "accessType": "Full"
  },
  {
    "id": "UgaL41FWQ0qx0Z4CK5jssA",
    "time": "2021-01-24T14:15:22Z",
    "serialNumber": "209356",
    "imei": "1088310383288683021",
    "lastLocation": {
      "lat": -42.792091,
      "lon": 146.909608,
      "date": "2021-01-23T08:01:54Z",
      "alt": 12
    },
    "owner" : {
      "email": "somebody@email.com",
    },
    "accessType": "Readonly"
  },
  {
    "id": "l7D4XDcIq0mZdCNBWm3yhA",
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
## Получить устройство по id в аккаунте

`GET https://service.iridium360.ru/rockstar-public/api/v1/devices/{id}`

> **Данный метод принимает id или серийный номер. 
> По id можно получить устройства, которыми владеет текущий аккаунт, а также устройства к которым предоставлен доступ. **Это рекомендуемый способ.**
> 
> По серийному номеру можно получить только устройства, владельцем которых является текущий аккаунт. **Это устаревший способ.**
> 
> Это правило распространяется и на остальные API методы

<h3 id="get__rockstar-public_api_v1_devices_{id}-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательный|Описание|
|---|---|---|---|---|
|id|path|string|да|Id устройства**|
|service-session|header|string|да|API токен|


<h3 id="get__rockstar-public_api_v1_devices_{id}-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiDeviceView](#apideviceview)|


> Пример ответа

```json
{
    "id": "UgaL41FWQ0qx0Z4CK5jssA",
    "time": "2021-01-24T14:15:22Z",
    "serialNumber": "209356",
    "imei": "1088310383288683021",
    "lastLocation": {
      "lat": -42.792091,
      "lon": 146.909608,
      "date": "2021-01-23T08:01:54Z",
      "alt": 12
    },
    "owner" : {
      "email": "example@email.com",
    },
    "accessType": "Full"
}
```

***
## Получить список точек устройства

`GET https://service.iridium360.ru/rockstar-public/api/v1/points`

<h3 id="get__rockstar-public_api_v1_points-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательный|Описание|
|---|---|---|---|---|
|id|query|string|да|Id устройства**|
|start|query|string(date-time)|нет|Дата (вкл) с которой выдать точки|
|end|query|string(date-time)|нет|Дата (вкл) до которой выдать точки|
|count|query|integer(int32)|нет|Максимальное кол-во выдаваемых точек|
|service-session|header|string|да|API токен|


<h3 id="get__rockstar-public_api_v1_points-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|array [[ApiDevicePointView](#apidevicepointview)]|

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
## Получить инфу о точке устройства

`GET https://service.iridium360.ru/rockstar-public/api/v1/points/{id}`

<h3 id="get__rockstar-public_api_v1_points_{id}-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательный|Описание|
|---|---|---|---|---|
|id|path|string|да|Id точки|
|service-session|header|string|да|API токен|


<h3 id="get__rockstar-public_api_v1_points_{id}-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiDevicePointView](#apidevicepointview)|

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
## Получить сообщения отправленные / полученные с устройства

`GET https://service.iridium360.ru/rockstar-public/api/v1/messages`

<h3 id="get__rockstar-public_api_v1_messages-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательный|Описание|
|---|---|---|---|---|
|id|query|string|да|Id устройства**|
|startId|query|string|нет|Id сообщения (включительно), с которого нужно выдать сообщения|
|count|query|integer(int32)|нет|Кол-во сообщений|
|service-session|header|string|да|API токен|


<h3 id="get__rockstar-public_api_v1_messages-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|array [[ApiMessageView](#apimessageview)]|

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
## Получить сообщение по id, а также его дочерние сообщения (при их наличии)

`GET https://service.iridium360.ru/rockstar-public/api/v1/messages/{id}`

<h3 id="get__rockstar-public_api_v1_messages_{id}-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательный|Описание|
|---|---|---|---|---|
|id|path|string|да|Id сообщения|
|service-session|header|string|да|API токен|


<h3 id="get__rockstar-public_api_v1_messages_{id}-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiMessageView](#apimessageview)|

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
## Отправить сообщение на устройство

`POST https://service.iridium360.ru/rockstar-public/api/v1/messages/send`

> Сообщение будет отправлено в приложение **Iridium360° Connect** (скачать для [Android](https://play.google.com/store/apps/details?id=ru.iridium360.connect) и [iOS](https://apps.apple.com/us/app/iridium360-connect/id1471545416))


<h3 id="post__rockstar-public_api_v1_messages_send-parameters">Параметры</h3>

|Имя|Расположение|Тип|Обязательный|Описание|
|---|---|---|---|---|
|id|query|string|да|Id устройства**|
|useMobileNumber|query|boolean|нет|Использовать мобильный номер аккаунта в качестве отправителя сообщения. По умолчанию используется email аккаунта|
|service-session|header|string|да|API токен|
|-|body|string|да|Текст сообщения|

<h3 id="post__rockstar-public_api_v1_messages_send-responses">Ответ</h3>

|Код|Статус|Описание|Формат ответа|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ApiMessageView](#apimessageview)|

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

```json
{
  "username": "string",
  "email": "string",
  "phone": "string",
  "avatar": "string"
}

```

### Параметры

|Имя|Тип|Обязательный|Описание|
|---|---|---|---|
|username|string|да|Имя пользователя|
|email|string|да|Email|
|phone|string|нет|Номер мобильного телефона|
|avatar|string|нет|Ссылка на аватар|

<h2 id="tocS_ApiDevicePointView">ApiDevicePointView</h2>

*Структура, содержащая информацию о точке устройства*

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

|Имя|Тип|Обязательный|Описание|
|---|---|---|---|
|id|string|да|Id точки|
|location|[Location](#location)|да|Координаты точки|

<h2 id="tocS_ApiDeviceView">ApiDeviceView</h2>

*Структура, содержащая информацию об устройстве*

```json
{
  "id": "UgaL41FWQ0qx0Z4CK5jssA",
  "time": "2019-08-24T14:15:22Z",
  "serialNumber": "string",
  "imei": "string",
  "lastLocation": {
    "lat": 0,
    "lon": 0,
    "date": "2019-08-24T14:15:22Z",
    "alt": 0
  },
  "owner" : {
    "email": "string",
  },
  "accessType": "Full"
}

```

### Параметры

|Имя|Тип|Обязательный|Описание|
|---|---|---|---|
|id|string|да|Id устройства**|
|time|string(date-time)|да|Дата актуальности данных|
|serialNumber|string|да|Серийный номер устройства|
|imei|string|да|IMEI устройства|
|lastLocation|[Location](#location)|нет|Последнее известное местоположение устройства|
|owner|[ApiAccountView](#apiaccountaiew)|нет|Владелец устройства*|
|accessType|[DeviceAccessType](#deviceaccesstype)|нет|Доступ к устройству*|

> *Будет возвращена информация о владельце и предоставленных правах доступа к устройству, если текущий аккаунт не является владельцем устройства


<h2 id="tocS_ApiMessageView">ApiMessageView</h2>

*Структура, содержащая информацию о сообщении*

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

|Имя|Тип|Обязательный|Описание|
|---|---|---|---|
|id|string|да|Id сообщения|
|date|string(date-time)|да|Дата получения / отправки|
|text|string|да|Текст сообщения|
|direction|[MessageDirection](#messagedirection)|да|Направление сообщения|
|subscriber|string|нет|Отправитель / получатель|
|location|[Location](#location)|да|Координаты отправки сообщения|
|childs|array [[ApiMessageView](#apimessageview)]|нет|Дочерние сообщения*|

> *Одно сообщение, отправленное с устройства может быть доставлено нескольким получателям (например, на мобильный телефон и email) в завимости от настроек в личном кабинете

<h2 id="tocS_Location">Location</h2>

*Структура, содержащая координаты*

```json
{
  "lat": 0,
  "lon": 0,
  "date": "2019-08-24T14:15:22Z",
  "alt": 0
}

```

### Параметры

|Имя|Тип|Обязательный|Описание|
|---|---|---|---|
|lat|number(double)|да|Широта|
|lon|number(double)|да|Долгота|
|date|string(date-time)|да|Дата|
|alt|number(double)|нет|Высота|

<h2 id="tocS_MessageDirection">MessageDirection</h2>

*Направление сообщения*


#### Значения

|Значение|Описание|
|---|---|
|FromDevice|Сообщение с устройства|
|ToDevice|Сообщение на устройство|


<h2 id="tocS_MessageDirection">DeviceAccessType</h2>

*Доступ к устройству*


#### Значения

|Значение|Описание|
|---|---|
|Readonly|Только просмотр. Имеет доступ «только чтение» к тем устройствам, к которым ему дал доступ владелец|
|Full|Полный доступ. Имеет доступ ко всем устройствам, к которым ему дал доступ владелец|





