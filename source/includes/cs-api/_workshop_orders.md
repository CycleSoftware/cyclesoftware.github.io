# Workshop orders #

Read, create or update workshop orders

***Scope(s)***

- `resources`

## Workshop order (object)

| **Property**                                      | **Type**    |                            | **Description**                                                                                                                    |
|---------------------------------------------------|-------------|----------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| `workshop_order_id`                               | `integer`   | `readonly`                 | Workshop order ID e.g. `978070`                                                                                                    |
| `sales_order_id`                                  | `integer`   | `readonly`                 | Sales order ID e.g. `978070`                                                                                                       |
| `customer_id`                                     | `integer`   | `POST`                     | Customer ID e.g. `24`                                                                                                              |
| `store_id`                                        | `integer`   | `POST`                     | Store ID e.g. `1`                                                                                                                  |
| `repair_object_id`                                | `integer`   | `POST`                     | Repair object ID e.g. `1105`                                                                                                       |
| `is_active`                                       | `boolean`   | <code>POST&#124;PUT</code> | If deleted `false`                                                                                                                 |
| `reference_text`                                  | `string`    | `POST`                     | Own reference e.g. `work_number`                                                                                                   |
| `datetime_scheduled_start`                        | `datetime`  | <code>POST&#124;PUT</code> | Scheduled start e.g. `2023-03-07 12:13:47`                                                                                         |
| `datetime_scheduled_finished`                     | `datetime`  | `readonly`                 | Scheduled finished e.g. `2023-03-07 12:43:47`                                                                                      |
| `datetime_created`                                | `datetime`  | `readonly`                 | Created at e.g. `2023-03-07 12:13:47`                                                                                              |
| `datetime_modified`                               | `datetime`  | `readonly`                 | Modified at e.g. `2023-03-07 12:13:47`                                                                                             |
| `mechanic_employee_id`                            | `integer`   | <code>POST&#124;PUT</code> | Employee ID of mechanic (see common employees) e.g. `12`                                                                           |
| `created_by_employee_id`                          | `integer`   | `POST`                     | Created by employee ID (see common employees) e.g. `1`                                                                             |
| `last_update_employee_id`                         | `integer`   | `POST`                     | Last update by employee ID (see common employees) e.g. `1`                                                                         |
| `phone_number_id`                                 | `string`    | `POST`                     | Phone number ID for communication e.g. `tel`                                                                                       |
| `repair_description`                              | `string`    | `POST`                     | Description of repair e.g. `posted repair`                                                                                         |
| `status_id`                                       | `integer`   | `POST`                     | Status see common enum `workshop_order_status` e.g. `7`                                                                            |
| `status_text`                                     | `string`    | `readonly`                 | Status text see common enum `workshop_order_status` e.g. `Reparatie voltooid`                                                      |
| `invoice_number`                                  | `integer`   | `readonly`                 | Sales transaction / invoice number `0` if not invoiced                                                                             |
| `borrowed_object_reference`                       | `string`    | <code>POST&#124;PUT</code> | Borrowed object reference                                                                                                          |
| `total_repair_time_minutes`                       | `integer`   | `readonly`                 | Total repair time scheduled in minutes e.g. `30`                                                                                   |
| `custom_repair_time_minutes`                      | `integer`   | `POST`                     | Custom repair time (total time - repair codes time) e.g. `30`                                                                      |
| `repair_codes`                                    | `?string[]` | `POST`                     | On create a list of repair codes. See [Repair codes (object)](#workshop-repair-codes) `code`                                       |
| `service_card_codes`                              | `?string[]` | `POST`                     | On create a list of service-item codes. See [Service item (object)](#workshop-service-items-service-item-object) `service_barcode` |
| `delivery_method_id`                              | `integer`   | <code>POST&#124;PUT</code> | Delivery method see common enum `delivery_methods` e.g. `0`                                                                        |
| `workshop_order_type_id`                          | `integer`   | `readonly`                 | Workshop order type id see common enum `workshop_order_types` e.g. `1`                                                             |
| `order_items`                                     | `?array`    | <code>POST&#124;PUT</code> | Array of order items                                                                                                               |
| `order_items[].item_id`                           | `integer`   | `readonly`                 | Unique item id within the order e.g. `2`                                                                                           |
| `order_items[].item_type_id`                      | `integer`   | <code>POST&#124;PUT</code> | Order item type see common enum `transaction_item_types` e.g. `1`                                                                  |
| `order_items[].special_type_id`                   | `integer`   | <code>POST&#124;PUT</code> | Related id for example object id e.g. `0`                                                                                          |
| `order_items[].quantity`                          | `integer`   | <code>POST&#124;PUT</code> | Quantity e.g. `1`                                                                                                                  |
| `order_items[].barcode`                           | `string`    | <code>POST&#124;PUT</code> | Barcode of item e.g. `102`                                                                                                         |
| `order_items[].pos_group_id`                      | `integer`   | <code>POST&#124;PUT</code> | POS group see common enum `pos_groups` e.g. `2`                                                                                    |
| `order_items[].description`                       | `string`    | <code>POST&#124;PUT</code> | Description of item e.g. `In- en uitbouwen electromotor in- en uitbouwen accu`                                                     |
| `order_items[].unit_price_in_vat_cents`           | `integer`   | <code>POST&#124;PUT</code> | Gross unit price including vat in cents e.g. `9000`                                                                                |
| `order_items[].unit_discount_amount_in_vat_cents` | `integer`   | <code>POST&#124;PUT</code> | Unit discount amount including VAT in cents e.g. `0`                                                                               |
| `order_items[].price_in_vat_cents`                | `integer`   | <code>POST&#124;PUT</code> | Line price including VAT in cents e.g. `9000`                                                                                      |
| `order_items[].discount_percentage`               | `decimal`   | <code>POST&#124;PUT</code> | Discount percentage e.g. `0`                                                                                                       |
| `order_items[].vat_code`                          | `integer`   | <code>POST&#124;PUT</code> | Vat code see common enum `vat_codes` e.g. `1`                                                                                      |
| `order_items[].vat_percentage`                    | `integer`   | `readonly`                 | Vat percentage e.g. `9`                                                                                                            |
| `order_items[].vat_amount_cents`                  | `integer`   | `readonly`                 | Line vat amount in cents e.g. `743`                                                                                                |
| `order_items[].item_status_id`                    | `integer`   | <code>POST&#124;PUT</code> | Status ID of item see common enum `sales_order_item_status` e.g. `0`                                                               |
| `order_items[].item_status_text`                  | `string`    | `readonly`                 | Status text of item see common enum `sales_order_item_status` e.g. `Geen status`                                                   |
| `order_items[].unit_work_time_minutes`            | `integer`   | <code>POST&#124;PUT</code> | Unit of work time in minutes e.g. `0`                                                                                              |
| `order_items[].assigned_to_customer_id`           | `integer`   | <code>POST&#124;PUT</code> | The customer ID which will receive the e.g. `1006` (Split order / invoicing)                                                       |
| `order_items[].invoice_number`                    | `?integer`  | `readonly`                 | Invoice number when invoice is created e.g. `20230303`                                                                             |

## List workshop orders

List workshop orders for a specific customer

@TODO

## Get workshop order

Get workshop order

> HTTP request

```http
GET /api/v1/customers/24/workshop-order/978768.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 2814
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "workshop_order_id": 978768,
    "sales_order_id": 978768,
    "customer_id": 24,
    "store_id": 1,
    "repair_object_id": 1105,
    "is_active": true,
    "reference_text": "work_number",
    "datetime_scheduled_start": "2023-03-07 16:54:23",
    "datetime_scheduled_finished": "2023-03-07 17:54:23",
    "datetime_created": "2023-03-07 16:54:23",
    "datetime_modified": "2023-03-07 16:54:23",
    "mechanic_employee_id": 12,
    "created_by_employee_id": 1,
    "last_update_employee_id": 1,
    "phone_number_id": "tel",
    "repair_description": "posted repair",
    "status_id": 7,
    "status_text": "Reparatie voltooid",
    "invoice_number": 0,
    "borrowed_object_reference": "",
    "total_repair_time_minutes": 60,
    "custom_repair_time_minutes": 0,
    "delivery_method_id": 0,
    "workshop_order_type_id": 1,
    "order_items": [
        {
            "item_id": 1,
            "item_type_id": 4,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "102",
            "pos_group_id": 2,
            "description": "In- en uitbouwen electromotor in- en uitbouwen accu",
            "unit_price_in_vat_cents": 9000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 9000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 9,
            "vat_amount_cents": 743,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 0,
            "assigned_to_customer_id": 24
        },
        {
            "item_id": 2,
            "item_type_id": 1,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "102",
            "pos_group_id": 2,
            "description": "In- en uitbouwen electromotor in- en uitbouwen accu",
            "unit_price_in_vat_cents": 9000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 9000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 9,
            "vat_amount_cents": 743,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 0,
            "assigned_to_customer_id": 24
        },
        {
            "item_id": 3,
            "item_type_id": 4,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "999",
            "pos_group_id": 2,
            "description": "Test Title",
            "unit_price_in_vat_cents": 12000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 12000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 9,
            "vat_amount_cents": 991,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 60,
            "assigned_to_customer_id": 24
        }
    ]
}
```

## Create workshop order

Create a workshop order

> HTTP request

```http
POST /api/v1/customers/24/workshop-order.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8
Content-length: 2814

{
    "customer_id": 24,
    "store_id": null,
    "repair_object_id": 1105,
    "is_active": true,
    "reference_text": "work_number",
    "datetime_scheduled_start": "2023-03-07T16:56:32+01:00",
    "datetime_scheduled_finished": null,
    "datetime_created": null,
    "datetime_modified": null,
    "mechanic_employee_id": 12,
    "created_by_employee_id": null,
    "last_update_employee_id": null,
    "phone_number_id": "tel",
    "repair_description": "posted repair",
    "status_id": 7,
    "status_text": null,
    "invoice_number": null,
    "borrowed_object_reference": null,
    "total_repair_time_minutes": null,
    "custom_repair_time_minutes": null,
    "delivery_method_id": 0,
    "repair_codes": [
        "999"
    ],
    "service_card_codes": [],
    "order_items": [
        {
            "item_id": 1,
            "item_type_id": 4,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "102",
            "pos_group_id": 2,
            "description": "In- en uitbouwen electromotor in- en uitbouwen accu",
            "unit_price_in_vat_cents": 9000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 9000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 6,
            "vat_amount_cents": 509,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 0
        },
        {
            "item_id": 2,
            "item_type_id": 1,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "102",
            "pos_group_id": 2,
            "description": "In- en uitbouwen electromotor in- en uitbouwen accu",
            "unit_price_in_vat_cents": 9000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 9000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 6,
            "vat_amount_cents": 509,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 0
        }
    ]
}
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 2814
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "workshop_order_id": 978768,
    "sales_order_id": 978768,
    "customer_id": 24,
    "store_id": 1,
    "repair_object_id": 1105,
    "is_active": true,
    "reference_text": "work_number",
    "datetime_scheduled_start": "2023-03-07 16:54:23",
    "datetime_scheduled_finished": "2023-03-07 17:54:23",
    "datetime_created": "2023-03-07 16:54:23",
    "datetime_modified": "2023-03-07 16:54:23",
    "mechanic_employee_id": 12,
    "created_by_employee_id": 1,
    "last_update_employee_id": 1,
    "phone_number_id": "tel",
    "repair_description": "posted repair",
    "status_id": 7,
    "status_text": "Reparatie voltooid",
    "invoice_number": 0,
    "borrowed_object_reference": "",
    "total_repair_time_minutes": 60,
    "custom_repair_time_minutes": 0,
    "delivery_method_id": 0,
    "workshop_order_type_id": 1,
    "order_items": [
        {
            "item_id": 1,
            "item_type_id": 4,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "102",
            "pos_group_id": 2,
            "description": "In- en uitbouwen electromotor in- en uitbouwen accu",
            "unit_price_in_vat_cents": 9000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 9000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 9,
            "vat_amount_cents": 743,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 0
        },
        {
            "item_id": 2,
            "item_type_id": 1,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "102",
            "pos_group_id": 2,
            "description": "In- en uitbouwen electromotor in- en uitbouwen accu",
            "unit_price_in_vat_cents": 9000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 9000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 9,
            "vat_amount_cents": 743,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 0
        },
        {
            "item_id": 3,
            "item_type_id": 4,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "999",
            "pos_group_id": 2,
            "description": "Test Title",
            "unit_price_in_vat_cents": 12000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 12000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 9,
            "vat_amount_cents": 991,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 60
        }
    ]
}
```

## Update workshop order

Update a workshop order

> HTTP request

```http
PUT /api/v1/customers/24/workshop-order/397876.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic
Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8
Content-length: 2237

{
    "is_active": true,
    "datetime_scheduled_start": "2020-03-13 18:15:45",
    "mechanic_employee_id": 12,
    "borrowed_object_reference": "",
    "total_repair_time_minutes": 30,
    "delivery_method_id": 0,
    "order_items": [
        {
            "item_id": 1,
            "item_type_id": 4,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "102",
            "pos_group_id": 2,
            "description": "In- en uitbouwen electromotor in- en uitbouwen accu",
            "unit_price_in_vat_cents": 9000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 9000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 9,
            "vat_amount_cents": 743,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 0
        },
        {
            "item_id": 2,
            "item_type_id": 1,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "102",
            "pos_group_id": 2,
            "description": "In- en uitbouwen electromotor in- en uitbouwen accu",
            "unit_price_in_vat_cents": 9000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 9000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 9,
            "vat_amount_cents": 743,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 0
        }
    ]
}
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 2237
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "workshop_order_id": 397876,
    "sales_order_id": 397876,
    "customer_id": 24,
    "store_id": 1,
    "repair_object_id": 1105,
    "is_active": true,
    "reference_text": "work_number",
    "datetime_scheduled_start": "2020-03-13 18:15:45",
    "datetime_scheduled_finished": "2020-03-13 18:45:45",
    "datetime_created": "2020-03-13 18:15:44",
    "datetime_modified": "2023-03-07 16:48:43",
    "mechanic_employee_id": 12,
    "created_by_employee_id": 1,
    "last_update_employee_id": 1,
    "phone_number_id": "tel",
    "repair_description": "64075cdc1db73",
    "status_id": 7,
    "status_text": "Reparatie voltooid",
    "invoice_number": 0,
    "borrowed_object_reference": "",
    "total_repair_time_minutes": 30,
    "custom_repair_time_minutes": 30,
    "delivery_method_id": 0,
    "workshop_order_type_id": 1,
    "order_items": [
        {
            "item_id": 1,
            "item_type_id": 4,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "102",
            "pos_group_id": 2,
            "description": "In- en uitbouwen electromotor in- en uitbouwen accu",
            "unit_price_in_vat_cents": 9000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 9000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 9,
            "vat_amount_cents": 743,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 0
        },
        {
            "item_id": 2,
            "item_type_id": 1,
            "special_type_id": 0,
            "quantity": 1,
            "barcode": "102",
            "pos_group_id": 2,
            "description": "In- en uitbouwen electromotor in- en uitbouwen accu",
            "unit_price_in_vat_cents": 9000,
            "unit_discount_amount_in_vat_cents": 0,
            "price_in_vat_cents": 9000,
            "discount_percentage": 0,
            "vat_code": 1,
            "vat_percentage": 9,
            "vat_amount_cents": 743,
            "item_status_id": 0,
            "item_status_text": "Geen status",
            "unit_work_time_minutes": 0
        }
    ]
}
```

