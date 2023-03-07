# Workshop #

Access workshop related information such as trading hours, stores, workshop orders etc.

***Scope(s)***

- `resources`


## Trading hours (object)

| **Property**                                | **Type**    | **Nullable** | **Description**                                                                           |
|---------------------------------------------|-------------|--------------|-------------------------------------------------------------------------------------------|
| `date`                                      | `date`      | `false`      | Date e.g. `2023-03-21`                                                                    |
| `capacity_minutes`                          | `integer`   | `false`      | Capacity in minutes e.g. `780`                                                            |
| `scheduled_minutes`                         | `integer`   | `false`      | Scheduled workshop orders in minutes e.g. `0`                                             |
| `available_minutes`                         | `integer`   | `false`      | Available duration in minutes e.g. `780`                                                  |
| `timestamp_finished_twsc_repairs`           | `timestamp` | `false`      | Unix timestamp when the scheduled workshop-orders via api are done (`0` if not available) |
| `day_id`                                    | `integer`   | `false`      | Day number in the week Sunday=`0` and Saturday =`6` e.g. `2`                              |
| `week_no`                                   | `integer`   | `false`      | Week number e.g. `12`                                                                     |
| `is_closed`                                 | `boolean`   | `false`      | `true` if store closed e.g. `false`                                                       |
| `workshop_trading_hours`                    | `array`     | `false`      | Array of trading hours                                                                    |
| `workshop_trading_hours[].start`            | `string`    | `false`      | Start of trading hours e.g. `07:00`                                                       |
| `workshop_trading_hours[].finish`           | `string`    | `false`      | End of trading hours e.g. `19:45`                                                         |
| `workshop_trading_hours[].duration_minutes` | `integer`   | `false`      | Duration of trading hours in minutes e.g. `780`                                           |


## Trading hours

Workshop trading hours for default or specific store

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v1/workshop/trading-hours.json?store_id=:store_id&day_count=:day_count</h6>
    </div>
</div>

| **GET parameter** | **Type**  | **Description**                                     |
|-------------------|-----------|-----------------------------------------------------|
| `store_id`        | `integer` | Store ID to get info for .e.g `2`                   |
| `day_count`       | `integer` | Number of days to retrieve information for e.g. `3` |

### Properties

The response is an array of Trading hours objects.

> HTTP request

```http
GET /api/v1/workshop/trading-hours.json?store_id=1&day_count=2 HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 5318

[
    {
        "date": "2023-03-08",
        "capacity_minutes": 780,
        "scheduled_minutes": 0,
        "available_minutes": 780,
        "timestamp_finished_twsc_repairs": 0,
        "day_id": 3,
        "week_no": 10,
        "is_closed": false,
        "workshop_trading_hours": [
            {
                "start": "07:00",
                "finish": "19:45",
                "duration_minutes": 780
            }
        ]
    },
    {
        "date": "2023-03-09",
        "capacity_minutes": 780,
        "scheduled_minutes": 0,
        "available_minutes": 780,
        "timestamp_finished_twsc_repairs": 0,
        "day_id": 4,
        "week_no": 10,
        "is_closed": false,
        "workshop_trading_hours": [
            {
                "start": "07:00",
                "finish": "19:45",
                "duration_minutes": 780
            }
        ]
    }
]
```

## Trading hours per store

Get the workshop trading hours per store

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v1/workshop/trading-hours-per-store.json?day_count=:day_count</h6>
    </div>
</div>

| **GET parameter** | **Type**  | **Description**                                     |
|-------------------|-----------|-----------------------------------------------------|
| `day_count`       | `integer` | Number of days to retrieve information for e.g. `3` |


### Properties

| **Property**                                                   | **Type**  | **Nullable** | **Description**                |
|----------------------------------------------------------------|-----------|--------------|--------------------------------|
| `[].store_id`                                                  | `integer` | `false`      | Store ID e.g. `2`              |
| `[].store_name`                                                | `string`  | `false`      | Store Name e.g. `Store 1`      |
| `[].trading_hours`                                             | `array`   | `false`      | array of Trading hours objects |


> HTTP request

```http
GET /api/v1/workshop/trading-hours-per-store.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 7150

[
    {
        "store_id": 1,
        "store_name": "Store 1",
        "trading_hours": [
            {
                "date": "2023-03-08",
                "capacity_minutes": 780,
                "scheduled_minutes": 0,
                "available_minutes": 780,
                "timestamp_finished_twsc_repairs": 0,
                "day_id": 3,
                "week_no": 10,
                "is_closed": false,
                "workshop_trading_hours": [
                    {
                        "start": "07:00",
                        "finish": "19:45",
                        "duration_minutes": 780
                    }
                ]
            },
            {
                "date": "2023-03-09",
                "capacity_minutes": 780,
                "scheduled_minutes": 0,
                "available_minutes": 780,
                "timestamp_finished_twsc_repairs": 0,
                "day_id": 4,
                "week_no": 10,
                "is_closed": false,
                "workshop_trading_hours": [
                    {
                        "start": "07:00",
                        "finish": "19:45",
                        "duration_minutes": 780
                    }
                ]
            }
        ]
    },
    {
        "store_id": 2,
        "store_name": "Store 2",
        "trading_hours": [
         {
                "date": "2023-03-08",
                "capacity_minutes": 780,
                "scheduled_minutes": 0,
                "available_minutes": 780,
                "timestamp_finished_twsc_repairs": 0,
                "day_id": 3,
                "week_no": 10,
                "is_closed": false,
                "workshop_trading_hours": [
                    {
                        "start": "07:00",
                        "finish": "19:45",
                        "duration_minutes": 780
                    }
                ]
            },
            {
                "date": "2023-03-09",
                "capacity_minutes": 780,
                "scheduled_minutes": 0,
                "available_minutes": 780,
                "timestamp_finished_twsc_repairs": 0,
                "day_id": 4,
                "week_no": 10,
                "is_closed": false,
                "workshop_trading_hours": [
                    {
                        "start": "07:00",
                        "finish": "19:45",
                        "duration_minutes": 780
                    }
                ]
            }
        ]
    }
]
```

## Repair codes

Get list of repair codes

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v1/workshop/repair-codes.json</h6>
    </div>
</div>

### Repair code (object)

| **Property**   | **Type**  | **Nullable** | **Description**                                        |
|----------------|-----------|--------------|--------------------------------------------------------|
| `code_id`    | `integer` | `false`      | ID of repair code e.g. `90753`                         |
| `category`   | `string`  | `false`      | Category name e.g. `Accu`                              |
| `code`       | `string`  | `false`      | Code e.g. `999`                                        |
| `description` | `string`  | `false`      | Description e.g. `Test Title`                          |
| `extra_text` | `string`  | `false`      | Description extra e.g. `Omschrijving`                  |
| `price_cents` | `integer` | `true`       | Price in cents or null e.g. `12000`                    |
| `time_minutes` | `integer` | `false`      | Time in minutes required for code e.g. `60`            |
| `workshop_rate_id` | `integer` | `false`      | Workshop rate see common api `workshop_rates` e.g. `1` |
| `vat_code`   | `integer` | `false`      | Vat code see common api `vat_codes` e.g. `1`           |

The result will return a list of Repair code (object)

> HTTP request

```http
GET /api/v1/workshop/repair-codes.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 278

[
    {
        "code_id": 90753,
        "category": "Accu",
        "code": "999",
        "description": "Test Title",
        "extra_text": "Omschrijving",
        "price_cents": 12000,
        "time_minutes": 60,
        "workshop_rate_id": 1,
        "vat_code": 1
    },
     {
        "code_id": 90753,
        "category": "Frame",
        "code": "222",
        "description": "Test Title",
        "extra_text": "Omschrijving",
        "price_cents": null,
        "time_minutes": 60,
        "workshop_rate_id": 1,
        "vat_code": 1
    }
]
```
