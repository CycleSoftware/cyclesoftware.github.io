# Workshop #

Access workshop related information such as trading hours, stores, workshop orders etc.

***Scope(s)***

- `resources`


## Trading hours (object)

| **Property**                                                     | **Type**    | **Description**                                                                                                                                                             |
|------------------------------------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `date`                                                           | `date`      | Date e.g. `2023-03-21`                                                                                                                                                      |
| `capacity_minutes`                                               | `integer`   | Capacity in minutes for online scheduling e.g. `780`                                                                                                                        |
| `scheduled_minutes`                                              | `integer`   | Scheduled workshop orders in minutes e.g. `0`                                                                                                                               |
| `available_minutes`                                              | `integer`   | Available time in workshop for online scheduling duration in minutes e.g. `780`                                                                                             |
| `day_id`                                                         | `integer`   | Day number in the week Sunday=`0` and Saturday =`6` e.g. `2`                                                                                                                |
| `week_no`                                                        | `integer`   | Week number e.g. `12`                                                                                                                                                       |
| `is_closed`                                                      | `boolean`   | `true` if store closed e.g. `false`                                                                                                                                         |
| `workshop_trading_hours`                                         | `object[]`  | Array of trading hours                                                                                                                                                      |
| `workshop_trading_hours[].start`                                 | `string`    | Start of trading hours e.g. `07:00`                                                                                                                                         |
| `workshop_trading_hours[].finish`                                | `string`    | End of trading hours e.g. `19:45`                                                                                                                                           |
| `workshop_trading_hours[].duration_minutes`                      | `integer`   | Duration of trading hours in minutes e.g. `780`                                                                                                                             |
| `availability_per_employee`                                      | `object[]`  | Availability per employee (since version `v2`)                                                                                                                              |
| `availability_per_employee[].employee_id`                        | `integer`   | Employee ID e.g. `56768` (see employees endpoint)                                                                                                                           |
| `availability_per_employee[].capacity_minutes`                   | `integer`   | The capacity in minutes availble for online scheduling e.g. `302`                                                                                                           |
| `availability_per_employee[].scheduled_minutes`                  | `integer`   | The sum of workshop orders total time in minutes e.g. `0`                                                                                                                   |
| `availability_per_employee[].available_minutes`                  | `integer`   | The available minutes for online scheduling e.g. `302`                                                                                                                      |
| `availability_per_employee[].available_slots`                    | `object[]`  | List of available time blocks. The blocks are blocked if a workshop order is scheduled. If workshop orders overlap, extra blocks are marked unavailable.                    |
| `availability_per_employee[].available_slots[].start`            | `string`    | Start time of available block e.g. `07:30`                                                                                                                                  |
| `availability_per_employee[].available_slots[].finish`           | `string`    | End time of available block e.g. `20:30`                                                                                                                                    |
| `availability_per_employee[].available_slots[].duration_minutes` | `integer`   | The duration of the available block in minutes e.g. `780` (if the employee is not fully available for online scheduling, this time might be higher than `available_minutes` |

## Trading hours

Workshop trading hours for default or specific store

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v2/workshop/trading-hours.json?store_id=:store_id&day_count=:day_count</h6>
    </div>
</div>

| **GET parameter** | **Type**  | **Description**                                     |
|-------------------|-----------|-----------------------------------------------------|
| `store_id`        | `integer` | Store ID to get info for .e.g `2`                   |
| `day_count`       | `integer` | Number of days to retrieve information for e.g. `3` |

### Properties

The response is an object with in `data` the trading hours objects.

> HTTP request

```http
GET /api/v2/workshop/trading-hours.json?store_id=1&day_count=2 HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 2224
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
  "data": [
    {
      "date": "2024-11-19",
      "capacity_minutes": 796,
      "scheduled_minutes": 0,
      "available_minutes": 796,
      "day_id": 2,
      "week_no": 47,
      "is_closed": false,
      "workshop_trading_hours": [
        {
          "start": "07:30",
          "finish": "20:15",
          "duration_minutes": 780
        }
      ],
      "availability_per_employee": [
        {
          "employee_id": 56768,
          "capacity_minutes": 302,
          "scheduled_minutes": 0,
          "available_minutes": 302,
          "available_slots": [
            {
              "start": "07:30",
              "finish": "20:30",
              "duration_minutes": 780
            }
          ]
        },
        {
          "employee_id": 1001,
          "capacity_minutes": 494,
          "scheduled_minutes": 0,
          "available_minutes": 494,
          "available_slots": [
            {
              "start": "07:30",
              "finish": "20:30",
              "duration_minutes": 780
            }
          ]
        }
      ]
    },
    {
      "date": "2024-11-20",
      "capacity_minutes": 780,
      "scheduled_minutes": 0,
      "available_minutes": 780,
      "day_id": 3,
      "week_no": 47,
      "is_closed": false,
      "workshop_trading_hours": [
        {
          "start": "07:30",
          "finish": "20:15",
          "duration_minutes": 780
        }
      ],
      "availability_per_employee": [
        {
          "employee_id": 56768,
          "capacity_minutes": 780,
          "scheduled_minutes": 0,
          "available_minutes": 780,
          "available_slots": [
            {
              "start": "07:30",
              "finish": "20:30",
              "duration_minutes": 780
            }
          ]
        },
        {
          "employee_id": 1001,
          "capacity_minutes": 0,
          "scheduled_minutes": 0,
          "available_minutes": 0,
          "available_slots": [
            {
              "start": "07:30",
              "finish": "20:30",
              "duration_minutes": 780
            }
          ]
        }
      ]
    }
  ]
}
```

## Trading hours per store

Get the workshop trading hours per store

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v2/workshop/trading-hours-per-store.json?day_count=:day_count&offset=:offset</h6>
    </div>
</div>

| **GET parameter** | **Type**  | **Description**                                           |
|-------------------|-----------|-----------------------------------------------------------|
| `day_count`       | `integer` | Number of days to retrieve information for e.g. `3`       |
| `offset`          | `integer` | Offset given in `pagination.next_url` pagination e.g. `3` |


### Properties

| **Property**           | **Type**   | **Description**                                                |
|------------------------|------------|----------------------------------------------------------------|
| `data[].store_id`      | `integer`  | Store ID e.g. `2`                                              |
| `data[].store_name`    | `string`   | Store Name e.g. `Store 1`                                      |
| `data[].trading_hours` | `object[]` | array of Trading hours objects                                 |
| `pagination.next_url`  | `?string`  | If there is more data this is the URL to the next API request. |



> HTTP request

```http
GET /api/v2/workshop/trading-hours-per-store.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 6075
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "data": [
        {
            "store_id": 1,
            "store_name": "Cycle Store 1",
            "trading_hours": [
                {
                    "date": "2024-11-19",
                    "capacity_minutes": 796,
                    "scheduled_minutes": 0,
                    "available_minutes": 796,
                    "day_id": 2,
                    "week_no": 47,
                    "is_closed": false,
                    "workshop_trading_hours": [
                        {
                            "start": "07:30",
                            "finish": "20:15",
                            "duration_minutes": 780
                        }
                    ],
                    "availability_per_employee": [
                        {
                            "employee_id": 56768,
                            "capacity_minutes": 302,
                            "scheduled_minutes": 0,
                            "available_minutes": 302,
                            "available_slots": [
                                {
                                    "start": "07:30",
                                    "finish": "20:30",
                                    "duration_minutes": 780
                                }
                            ]
                        },
                        {
                            "employee_id": 1001,
                            "capacity_minutes": 494,
                            "scheduled_minutes": 0,
                            "available_minutes": 494,
                            "available_slots": [
                                {
                                    "start": "07:30",
                                    "finish": "20:30",
                                    "duration_minutes": 780
                                }
                            ]
                        }
                    ]
                },
                {
                    "date": "2024-11-20",
                    "capacity_minutes": 780,
                    "scheduled_minutes": 0,
                    "available_minutes": 780,
                    "day_id": 3,
                    "week_no": 47,
                    "is_closed": false,
                    "workshop_trading_hours": [
                        {
                            "start": "07:30",
                            "finish": "20:15",
                            "duration_minutes": 780
                        }
                    ],
                    "availability_per_employee": [
                        {
                            "employee_id": 56768,
                            "capacity_minutes": 780,
                            "scheduled_minutes": 0,
                            "available_minutes": 780,
                            "available_slots": [
                                {
                                    "start": "07:30",
                                    "finish": "20:30",
                                    "duration_minutes": 780
                                }
                            ]
                        },
                        {
                            "employee_id": 1001,
                            "capacity_minutes": 0,
                            "scheduled_minutes": 0,
                            "available_minutes": 0,
                            "available_slots": [
                                {
                                    "start": "07:30",
                                    "finish": "20:30",
                                    "duration_minutes": 780
                                }
                            ]
                        }
                    ]
                }
            ]
        },
        {
            "store_id": 2,
            "store_name": "Cycle Store 2",
            "trading_hours": [
                {
                    "date": "2024-11-20",
                    "capacity_minutes": 780,
                    "scheduled_minutes": 0,
                    "available_minutes": 780,
                    "day_id": 3,
                    "week_no": 47,
                    "is_closed": false,
                    "workshop_trading_hours": [
                        {
                            "start": "07:30",
                            "finish": "20:15",
                            "duration_minutes": 780
                        }
                    ],
                    "availability_per_employee": [
                        {
                            "employee_id": 526768,
                            "capacity_minutes": 780,
                            "scheduled_minutes": 0,
                            "available_minutes": 780,
                            "available_slots": [
                                {
                                    "start": "07:30",
                                    "finish": "20:30",
                                    "duration_minutes": 780
                                }
                            ]
                        },
                        {
                            "employee_id": 10201,
                            "capacity_minutes": 0,
                            "scheduled_minutes": 0,
                            "available_minutes": 0,
                            "available_slots": [
                                {
                                    "start": "07:30",
                                    "finish": "20:30",
                                    "duration_minutes": 780
                                }
                            ]
                        }
                    ]
                }
            ]
        },
        {
            "store_id": 3,
            "store_name": "DC",
            "trading_hours": []
        }
    ],
    "pagination": {
        "next_url": null
    }
}
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

| **Property**       | **Type**   | **Description**                                        |
|--------------------|------------|--------------------------------------------------------|
| `code_id`          | `integer`  | ID of repair code e.g. `90753`                         |
| `category`         | `string`   | Category name e.g. `Accu`                              |
| `code`             | `string`   | Code e.g. `999`                                        |
| `description`      | `string`   | Description e.g. `Test Title`                          |
| `extra_text`       | `string`   | Description extra e.g. `Omschrijving`                  |
| `price_cents`      | `?integer` | Price in cents or null e.g. `12000`                    |
| `time_minutes`     | `integer`  | Time in minutes required for code e.g. `60`            |
| `workshop_rate_id` | `integer`  | Workshop rate see common api `workshop_rates` e.g. `1` |
| `vat_code`         | `integer`  | Vat code see common api `vat_codes` e.g. `1`           |

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
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

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
