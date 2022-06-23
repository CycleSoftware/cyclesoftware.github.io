# Workshop #

Access workshop related data

***Authentication mechanism***

- Basic HTTP Authentication
- Scopes: `salesdata`

## Service items ##

Get list of service items for workshop.

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

| Property                               | Type       | Nullable | Description                                                                           |
|----------------------------------------|------------|----------|---------------------------------------------------------------------------------------|
| `error`                                | `boolean`  | `false`  | e.g. `false`                                                                          |
| `error_message`                        | `string`   | `true`   | if not null the error message                                                         |
| `data`                                 | `array`    | `false`  | Array of service item objects                                                         |
| `data[].service_id`                    | `integer`  | `false`  | ID of service `1790811`                                                               |
| `data[].service_item_id`               | `integer`  | `false`  | Iem ID of service item `4823371`                                                      |
| `data[].service_barcode`               | `string`   | `false`  | Barcode of service item e.g. `DSK-1790811-3`                                          |
| `data[].service_status_id`             | `integer`  | `false`  | Service status see common api `service_item_status` e.g. `1`                          |
| `data[].invoice_number`                | `integer`  | `false`  | If positive number, the invoice which triggered creation of this item e.g. `20173208` |
| `data[].customer_id`                   | `integer`  | `false`  | ID of customer e.g. `235269422`                                                       |
| `data[].object_id`                     | `integer`  | `false`  | ID of object e.g. `24136`                                                             |
| `data[].is_open`                       | `boolean`  | `false`  | `true` if still open                                                                  |
| `data[].is_scheduled`                  | `boolean`  | `false`  | `true` if scheduled in a workshop order                                               |
| `data[].title`                         | `string`   | `false`  | Title e.g. `3e servicebeurt`                                                          |
| `data[].description`                   | `string`   | `false`  | Description e.g. `3e servicebeurt`                                                    |
| `data[].gross_unit_price_cents`        | `integer`  | `false`  | Gross price in cents `6900`                                                           |
| `data[].unit_discount_amount_cents`    | `integer`  | `false`  | Discount in cents `0`                                                                 |
| `data[].amount_payed_in_advance_cents` | `integer`  | `false`  | Amount payed `0`                                                                      |
| `data[].time_minutes`                  | `integer`  | `false`  | Time in minutes for workshop `60`                                                     |
| `data[].scheduled_at`                  | `date`     | `false`  | Scheduled for date e.g. `2021-12-22`                                                  |
| `data[].scheduled_at_km_age`           | `integer`  | `false`  | Scheduled after X kilometer                                                           |
| `data[].modified_at`                   | `datetime` | `false`  | Modification date time `2020-06-22 10:51:49`                                          |
| `pagination.count`                     | `integer`  | `false`  | Count of results                                                                      |
| `pagination.next_offset`               | `integer`  | `true`   | null if no next page available, otherwise value for `offset` GET variable             |

```http
GET /api/v1/workshop/repair-objects/service-items.json?modified_start=2022-06-01&modified_end=2022-06-25 HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 2366

{
    "error": false,
    "error_message": null,
    "data": [
        {
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
            "service_id": 1790811,
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
            "service_id": 1790811,
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
