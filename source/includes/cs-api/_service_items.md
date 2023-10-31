# Service items #

Read, create or update repair objects for a customer

***Scope(s)***

- `resources`

## Service item (object)

| **Property**                    | **Type**   | **Description**                                                                       |
|---------------------------------|------------|---------------------------------------------------------------------------------------|
| `account_id`                    | `integer`  | Account ID within CS `1000`                                                           |
| `store_id`                      | `integer`  | Store ID of service item `1`                                                          |
| `service_id`                    | `integer`  | ID of service `1790811`                                                               |
| `service_item_id`               | `integer`  | Iem ID of service item `4823371`                                                      |
| `service_barcode`               | `string`   | Barcode of service item e.g. `DSK-1790811-3`                                          |
| `service_status_id`             | `integer`  | Service status see common api `service_item_status` e.g. `1`                          |
| `invoice_number`                | `integer`  | If positive number, the invoice which triggered creation of this item e.g. `20173208` |
| `customer_id`                   | `integer`  | ID of customer e.g. `235269422`                                                       |
| `object_id`                     | `integer`  | ID of object e.g. `24136`                                                             |
| `is_open`                       | `boolean`  | `true` if still open                                                                  |
| `is_scheduled`                  | `boolean`  | `true` if scheduled in a workshop order                                               |
| `title`                         | `string`   | Title e.g. `3e servicebeurt`                                                          |
| `description`                   | `string`   | Description e.g. `3e servicebeurt`                                                    |
| `gross_unit_price_cents`        | `integer`  | Gross unit price in cents `6900`                                                      |
| `unit_discount_amount_cents`    | `integer`  | Discount in cents `0`                                                                 |
| `amount_payed_in_advance_cents` | `integer`  | Amount payed `0`                                                                      |
| `time_minutes`                  | `integer`  | Time in minutes for workshop `60`                                                     |
| `scheduled_at`                  | `date`     | Scheduled for date e.g. `2021-12-22`                                                  |
| `scheduled_at_km_age`           | `integer`  | Scheduled after X kilometer                                                           |
| `modified_at`                   | `datetime` | Modification date time `2020-06-22 10:51:49`                                          |

## Service items for customer

Get service items for customer

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v1/customers/:customer_id/service-items.json</h6>
    </div>
</div>

| **URI parameter** | **Type** | **Description**         |
|-------------------|----------|-------------------------|
| `customer_id`     | `int`    | Customer ID e.g. `2001` |

> HTTP request

```http
GET /api/v1/customers/2/service-items.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 20471
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

[
    {
        "account_id": 5185,
        "store_id": 1,
        "service_id": 2302569,
        "service_item_id": 6786341,
        "service_barcode": "DSK-2302569-1",
        "service_status_id": 2,
        "invoice_number": 421236,
        "customer_id": 2001,
        "object_id": 175432,
        "is_open": true,
        "is_scheduled": false,
        "description": "test",
        "title": "test",
        "gross_unit_price_cents": 3200,
        "unit_discount_amount_cents": 2300,
        "amount_payed_in_advance_cents": 900,
        "time_minutes": 30,
        "scheduled_at": "2021-07-22",
        "scheduled_at_km_age": 0,
        "modified_at": "2021-07-22 07:00:16"
    },
    {
        "account_id": 5185,
        "store_id": 1,
        "service_id": 2302721,
        "service_item_id": 6786899,
        "service_barcode": "DSK-2302721-1",
        "service_status_id": 2001,
        "invoice_number": 421268,
        "customer_id": 2,
        "object_id": 175444,
        "is_open": true,
        "is_scheduled": false,
        "description": "test",
        "title": "test",
        "gross_unit_price_cents": 3200,
        "unit_discount_amount_cents": 2300,
        "amount_payed_in_advance_cents": 900,
        "time_minutes": 30,
        "scheduled_at": "2021-07-22",
        "scheduled_at_km_age": 0,
        "modified_at": "2021-07-22 07:00:16"
    }
]
```

## Service items

Get service items for service ID

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v1/customers/:customer_id/service-items/:service_id.json</h6>
    </div>
</div>

| **URI parameter** | **Type** | **Description**           |
|-------------------|----------|---------------------------|
| `customer_id`     | `int`    | Customer ID e.g. `2001`   |
| `service_id`      | `int`    | Service ID e.g. `2302569` |

> HTTP request

```http
GET /api/v1/customers/2001/service-items/2302569.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic
Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 662
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

[
    {
        "account_id": 5185,
        "store_id": 1,
        "service_id": 2302569,
        "service_item_id": 6786341,
        "service_barcode": "DSK-2302569-1",
        "service_status_id": 2,
        "invoice_number": 421236,
        "customer_id": 2001,
        "object_id": 175432,
        "is_open": true,
        "is_scheduled": false,
        "description": "test",
        "title": "test",
        "gross_unit_price_cents": 3200,
        "unit_discount_amount_cents": 2300,
        "amount_payed_in_advance_cents": 900,
        "time_minutes": 30,
        "scheduled_at": "2021-07-22",
        "scheduled_at_km_age": 0,
        "modified_at": "2021-07-22 07:00:16"
    },
    
    {
        "account_id": 5185,
        "store_id": 1,
        "service_id": 2302569,
        "service_item_id": 6786342,
        "service_barcode": "DSK-2302569-2",
        "service_status_id": 2,
        "invoice_number": 421236,
        "customer_id": 2001,
        "object_id": 175432,
        "is_open": true,
        "is_scheduled": false,
        "description": "test2",
        "title": "test2",
        "gross_unit_price_cents": 3200,
        "unit_discount_amount_cents": 2300,
        "amount_payed_in_advance_cents": 900,
        "time_minutes": 30,
        "scheduled_at": "2021-10-22",
        "scheduled_at_km_age": 300,
        "modified_at": "2021-07-22 07:00:16"
    }
]
```


## Service items list ##

Get list of service items for workshop.

- Scopes: `sales-export`

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/workshop/repair-objects/service-items.json</h6>
	</div>
</div>
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/workshop/repair-objects/service-items.json?modified_start=:modified_start&modified_end=:modified_end&offset=:offset</h6>
	</div>
</div>

| GET parameter    | Type      | Description                               |
|------------------|-----------|-------------------------------------------|
| `modified_start` | `date`    | end date e.g. 2020-01-01                  |
| `modified_end`   | `date`    | end date e.g. 2020-01-01                  |
| `offset`         | `integer` | offset (omit or `pagination.next_offset`) |


### Properties ###

| Property                               | Type       | Description                                                                           |
|----------------------------------------|------------|---------------------------------------------------------------------------------------|
| `error`                                | `boolean`  | e.g. `false`                                                                          |
| `error_message`                        | `?string`  | if not null the error message                                                         |
| `data`                                 | `object[]` | Array of service item objects                                                         |
| `data[].account_id`                    | `integer`  | Account ID within CS `1000`                                                           |
| `data[].store_id`                      | `integer`  | Store ID of associated to service item `1`                                            |
| `data[].service_id`                    | `integer`  | ID of service `1790811`                                                               |
| `data[].service_item_id`               | `integer`  | Iem ID of service item `4823371`                                                      |
| `data[].service_barcode`               | `string`   | Barcode of service item e.g. `DSK-1790811-3`                                          |
| `data[].service_status_id`             | `integer`  | Service status see common api `service_item_status` e.g. `1`                          |
| `data[].invoice_number`                | `integer`  | If positive number, the invoice which triggered creation of this item e.g. `20173208` |
| `data[].customer_id`                   | `integer`  | ID of customer e.g. `235269422`                                                       |
| `data[].object_id`                     | `integer`  | ID of object e.g. `24136`                                                             |
| `data[].is_open`                       | `boolean`  | `true` if still open                                                                  |
| `data[].is_scheduled`                  | `boolean`  | `true` if scheduled in a workshop order                                               |
| `data[].title`                         | `string`   | Title e.g. `3e servicebeurt`                                                          |
| `data[].description`                   | `string`   | Description e.g. `3e servicebeurt`                                                    |
| `data[].gross_unit_price_cents`        | `integer`  | Gross unit price in cents `6900`                                                      |
| `data[].unit_discount_amount_cents`    | `integer`  | Discount in cents `0`                                                                 |
| `data[].amount_payed_in_advance_cents` | `integer`  | Amount payed `0`                                                                      |
| `data[].time_minutes`                  | `integer`  | Time in minutes for workshop `60`                                                     |
| `data[].scheduled_at`                  | `date`     | Scheduled for date e.g. `2021-12-22`                                                  |
| `data[].scheduled_at_km_age`           | `integer`  | Scheduled after X kilometer                                                           |
| `data[].modified_at`                   | `datetime` | Modification date time `2020-06-22 10:51:49`                                          |
| `pagination.count`                     | `integer`  | Count of results                                                                      |
| `pagination.next_offset`               | `?integer` | `null` if no next page available, otherwise value for `offset` GET variable           |

```http
GET /api/v1/workshop/repair-objects/service-items.json?modified_start=2022-06-01&modified_end=2022-06-25 HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 2392
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "error": false,
    "error_message": null,
    "data": [
        {
            "account_id": 1000,
            "store_id": 1,
            "service_id": 1790811,
            "service_item_id": 4823367,
            "service_barcode": "DSK-1790811-1",
            "service_status_id": 1,
            "invoice_number": 20173208,
            "customer_id": 235269422,
            "object_id": 24136,
            "is_open": true,
            "is_scheduled": false,
            "title": "1e servicebeurt",
            "description": "1e servicebeurt",
            "gross_unit_price_cents": 8800,
            "unit_discount_amount_cents": 6900,
            "amount_payed_in_advance_cents": 0,
            "time_minutes": 30,
            "scheduled_at": "2022-09-22",
            "scheduled_at_km_age": 0,
            "modified_at": "2022-06-22 10:51:49"
        },
        {
            "account_id": 1000,
            "store_id": 1,
            "service_item_id": 4823369,
            "service_barcode": "DSK-1790811-2",
            "service_status_id": 1,
            "invoice_number": 20173208,
            "customer_id": 235269422,
            "object_id": 24136,
            "is_open": true,
            "is_scheduled": false,
            "title": "2e servicebeurt",
            "description": "2e servicebeurt",
            "gross_unit_price_cents": 6900,
            "unit_discount_amount_cents": 3400,
            "amount_payed_in_advance_cents": 0,
            "time_minutes": 30,
            "scheduled_at": "2022-06-22",
            "scheduled_at_km_age": 500,
            "modified_at": "2022-06-22 10:51:49"
        },
        {
            "account_id": 1000,
            "store_id": 1,
            "service_item_id": 4823371,
            "service_barcode": "DSK-1790811-3",
            "service_status_id": 1,
            "invoice_number": 20173208,
            "customer_id": 235269422,
            "object_id": 24136,
            "is_open": true,
            "is_scheduled": false,
            "title": "3e servicebeurt",
            "description": "3e servicebeurt",
            "gross_unit_price_cents": 6900,
            "unit_discount_amount_cents": 0,
            "amount_payed_in_advance_cents": 0,
            "time_minutes": 60,
            "scheduled_at": "2022-12-22",
            "scheduled_at_km_age": 0,
            "modified_at": "2022-06-22 10:51:49"
        }
    ],
    "pagination": {
        "count": 3,
        "next_offset": null
    }
}
```
