# eAsistent Mobile API Endpoints

*More endpoints coming soon*

### Login

Method: **POST**

URL: `https://www.easistent.com/m/login`

Request:

```json
{
    "username": "",
    "password": "",
    "supported_user_types": [
        "parent",
        "child"
    ]
}
```

Response:

```json
{
    "access_token": {
        "expiration_date": "2022-03-16T12:00:00+0100",
        "token": ""
    },
    "refresh_token": "",
    "user": {
        "freshPassword": null,
        "id": 123456,
        "language": "sl_SI",
        "name": "Janez",
        "type": "child",
        "username": "12345678"
    }
}
```

### Timetable

Method: **GET**

URL: `https://www.easistent.com/m/timetable/events?from=2022-01-01&to=2022-01-30`

Headers:

```
x-app-name: child
x-client-version: 11101
x-client-platform: android
app: new_mobile_app
authorization: Bearer <token>
```

Response:

```json
{
  "events": [
    {
      "classroom": "106",
      "color": "#4b4bbf",
      "date": "2021-12-13",
      "from": "07:30",
      "homework": [],
      "lesson": "rekurzija",
      "teachers": ["Janez Novak"],
      "title": "RPAv",
      "title_short": "RPAv",
      "to": "08:15",
      "type": "school_hour"
    }
  ]
}
```

---

### Refresh Token

Method: **POST**

URL: **`https://www.easistent.com/m/refresh_token`**

Headers:

```
x-app-name:	child
x-client-version: 11101
x-client-platform: android
app: new_mobile_app
cookie:	easistent_session=<session_token>
```

Request:

```json
{
  "refresh_token": "<refresh_token>"
}
```

Response:

```json
{
  "access_token": {
    "expiration_date": "<date>",
    "token": "<token>"
  },
  "refresh_token": "<refresh_token>"
}
```

---

### Get child

Method: **GET**

URL: `https://www.easistent.com/m/me/child`

Headers:

```
x-app-name: child
x-client-version: 11101
x-client-platform: android
app: new_mobile_app
authorization: Bearer <token>
```

Response:

```json
{
  "age": 69,
  "age_level": "zeroth",
  "avatar": null,
  "did_try_plus": true,
  "display_name": "Janez",
  "gender": "m",
  "id": 69420,
  "language": "sl_SI",
  "notifications": [],
  "plus_enabled": true,
  "short_name": "Jan",
  "student_id": 8189753,
  "timetable": {
    "date": "2021-12-16",
    "hours": [
      {
        "from": "2021-12-16T07:30:00",
        "metadata": [],
        "summary": "IDE-ZDV",
        "to": "2021-12-16T19:35:00",
        "type": "event"
      },
      {
        "from": "2021-12-16T19:35:00",
        "metadata": {
          "tomorrow_end": "13:30",
          "tomorrow_info": "Jutri",
          "tomorrow_normal": true,
          "tomorrow_start": "07:30"
        },
        "summary": "Konec pouka",
        "to": "2021-12-16T23:59:59",
        "type": "end_day"
      }
    ]
  },
  "trial": true,
  "trial_ends": "2022-01-13",
  "type": "child"
}
```
