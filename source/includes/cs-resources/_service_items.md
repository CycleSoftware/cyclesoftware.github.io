# Workshop service items #

Read, create or update repair objects for a customer

***Scope(s)***

- `resources`

## Service item (object)

| **Property**                    | **Type**   | **Nullable** | **Description**                                                                       |
|---------------------------------|------------|--------------|---------------------------------------------------------------------------------------|
| `account_id`                    | `integer`  | `false`      | Account ID within CS `1000`                                                           |
| `service_id`                    | `integer`  | `false`      | ID of service `1790811`                                                               |
| `service_item_id`               | `integer`  | `false`      | Iem ID of service item `4823371`                                                      |
| `service_barcode`               | `string`   | `false`      | Barcode of service item e.g. `DSK-1790811-3`                                          |
| `service_status_id`             | `integer`  | `false`      | Service status see common api `service_item_status` e.g. `1`                          |
| `invoice_number`                | `integer`  | `false`      | If positive number, the invoice which triggered creation of this item e.g. `20173208` |
| `customer_id`                   | `integer`  | `false`      | ID of customer e.g. `235269422`                                                       |
| `object_id`                     | `integer`  | `false`      | ID of object e.g. `24136`                                                             |
| `is_open`                       | `boolean`  | `false`      | `true` if still open                                                                  |
| `is_scheduled`                  | `boolean`  | `false`      | `true` if scheduled in a workshop order                                               |
| `title`                         | `string`   | `false`      | Title e.g. `3e servicebeurt`                                                          |
| `description`                   | `string`   | `false`      | Description e.g. `3e servicebeurt`                                                    |
| `gross_unit_price_cents`        | `integer`  | `false`      | Gross price in cents `6900`                                                           |
| `unit_discount_amount_cents`    | `integer`  | `false`      | Discount in cents `0`                                                                 |
| `amount_payed_in_advance_cents` | `integer`  | `false`      | Amount payed `0`                                                                      |
| `time_minutes`                  | `integer`  | `false`      | Time in minutes for workshop `60`                                                     |
| `scheduled_at`                  | `date`     | `false`      | Scheduled for date e.g. `2021-12-22`                                                  |
| `scheduled_at_km_age`           | `integer`  | `false`      | Scheduled after X kilometer                                                           |
| `modified_at`                   | `datetime` | `false`      | Modification date time `2020-06-22 10:51:49`                                          |

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

[
    {
        "account_id": 5185,
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

[
    {
        "account_id": 5185,
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

## Service items list

