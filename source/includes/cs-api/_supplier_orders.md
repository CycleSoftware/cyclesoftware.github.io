# Supplier orders #

Create and send supplier orders

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `e-commerce`


### Supplier order (object)

Properties used in create, get and send endpoints.

| Property                          | Type       | POST   | Description                                                 |
|-----------------------------------|------------|--------|-------------------------------------------------------------|
| `supplier_order_id`               | `integer`  |        | Supplier order ID `2222`                                    |
| `supplier_id`                     | `integer`  | `POST` | Supplier ID see common suppliers endpoint e.g. `2113`       |
| `store_id`                        | `integer`  | `POST` | Store ID within account e.g. `2`                            |
| `order_type_id`                   | `integer`  |        | Order type see common enum supplier_order_types e.g. `1`    |
| `status_id`                       | `integer`  |        | Order status see common enum supplier_order_status e.g. `0` |
| `supplier_comment`                | `string`   |        | Comment given by supplier e.g. `Some text`                  |
| `supplier_reference`              | `string`   |        | Reference from supplier `ref-from-supplier`                 |
| `own_reference`                   | `string`   |        | Own reference e.g. `Own1212`                                |
| `created_at`                      | `datetime` |        | Creation date `2022-01-12 12:30:30`                         |
| `items`                           | `object[]` |        | Array of order items                                        |
| `items[].supplier_order_item_id`  | `integer`  |        | Item ID `10012`                                             |
| `items[].item_type_id`            | `integer`  |        | Item type see common enum transaction_item_types e.g. `1`   |
| `items[].article_id`              | `string`   | `POST` | Article Number. `ART2`                                      |
| `items[].barcode`                 | `string`   | `POST` | Barcode e.g. `BARCODE2`                                     |
| `items[].quantity`                | `integer`  | `POST` | Quantity ordered e.g. `2`                                   |
| `items[].quantity_delivered`      | `integer`  |        | Quantity delivered e.g. `0`                                 |
| `items[].quantity_open`           | `integer`  |        | Quantity open (not delivered) e.g. `2`                      |
| `items[].supplier_delivery_date`  | `date`     |        | Delivery date given by supplier e.g. `2022-01-20`           |
| `items[].supplier_item_reference` | `string`   |        | Reference item from supplier e.g. `ref-item-1`              |


## Create supplier order

Creates a supplier order. To actually dispatch and send the supplier order to the supplier call the send endpoint with the obtained supplier order ID.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/supplier/order.json</h6>
	</div>
</div>

> HTTP request

```http
POST /api/v1/supplier/order.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8
Content-length: 299

{
    "supplier_id": 2113,
    "store_id": 2,
    "own_reference": "ref1",
    "items": [
        {
            "barcode": "87123456789",
            "article_id": "art-no-1",
            "quantity": 1
        },
        {
            "barcode": "87123456790",
            "article_id": "art-no-2",
            "quantity": 2
        }
    ]
}
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 1017
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "supplier_order_id": 2222,
    "supplier_id": 2113,
    "store_id": 2,
    "order_type_id": 1,
    "status_id": 0,
    "supplier_comment": "Some text",
    "own_reference": "ref1",
    "supplier_reference": "ref-from-supplier",
    "created_at": "2022-01-12 12:30:30",
    "items": [
        {
            "supplier_order_item_id": 10010,
            "item_type_id": 1,
            "article_id": "art-no-1",
            "barcode": "87123456789",
            "quantity": 1,
            "quantity_delivered": 0,
            "quantity_open": 1,
            "supplier_delivery_date": null,
            "supplier_item_reference": ""
        },
        {
            "supplier_order_item_id": 10012,
            "item_type_id": 1,
            "article_id": "ART2",
            "barcode": "BARCODE2",
            "quantity": 2,
            "quantity_delivered": 0,
            "quantity_open": 2,
            "supplier_delivery_date": "2022-01-20",
            "supplier_item_reference": "ref-item-1"
        }
    ]
}
```

> HTTP Error Response

```http
HTTP/1.1 400 
Content-type: application/json; charset=utf-8
Content-length: 57
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "error": true,
    "error_message": "Bad request"
}
```

## Get supplier order

<div class="api-endpoint">
<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/supplier/order/:id.json</h6>
	</div>
</div>

> HTTP request

```http
GET /api/v1/supplier/order/2222.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 1022
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "supplier_order_id": 2222,
    "supplier_id": 2113,
    "store_id": 2,
    "order_type_id": 1,
    "status_id": 0,
    "supplier_comment": "Some text",
    "own_reference": "own-ref-1",
    "supplier_reference": "ref-from-supplier",
    "created_at": "2022-01-12 12:30:30",
    "items": [
        {
            "supplier_order_item_id": 10010,
            "item_type_id": 1,
            "article_id": "art-no-1",
            "barcode": "87123456789",
            "quantity": 1,
            "quantity_delivered": 0,
            "quantity_open": 1,
            "supplier_delivery_date": null,
            "supplier_item_reference": ""
        },
        {
            "supplier_order_item_id": 10012,
            "item_type_id": 1,
            "article_id": "ART2",
            "barcode": "BARCODE2",
            "quantity": 2,
            "quantity_delivered": 0,
            "quantity_open": 2,
            "supplier_delivery_date": "2022-01-20",
            "supplier_item_reference": "ref-item-1"
        }
    ]
}
```

## Send supplier order

Send a supplier order.

<div class="api-endpoint">
<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/supplier/order/:id/send.json</h6>
	</div>
</div>

> HTTP request

```http
POST /api/v1/supplier/order/2222.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 1023
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "supplier_order_id": 2222,
    "supplier_id": 2113,
    "store_id": 2,
    "order_type_id": 1,
    "status_id": 1,
    "supplier_comment": "Some text",
    "supplier_reference": "ref-from-supplier",
    "own_reference": "own-ref-1",
    "created_at": "2022-01-12 12:30:30",
    "items": [
        {
            "supplier_order_item_id": 10010,
            "item_type_id": 1,
            "article_id": "art-no-1",
            "barcode": "87123456789",
            "quantity": 1,
            "quantity_delivered": 0,
            "quantity_open": 1,
            "supplier_delivery_date": null,
            "supplier_item_reference": ""
        },
        {
            "supplier_order_item_id": 10012,
            "item_type_id": 1,
            "article_id": "ART2",
            "barcode": "BARCODE2",
            "quantity": 2,
            "quantity_delivered": 0,
            "quantity_open": 2,
            "supplier_delivery_date": "2022-01-20",
            "supplier_item_reference": "ref-item-1",
        }
    ]
}
```

> HTTP Error Response

```http
HTTP/1.1 400 
Content-type: application/json; charset=utf-8
Content-length: 57
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "error": true,
    "error_message": "Error given by supplier"
}
```



## Process dropshipment packinglist

Process a packinglist for a dropshipment. 

Be aware! The goods in the packinglist will not be added to the stock!


<div class="api-endpoint">
<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/supplier/packinglist/process-dropshipment.json</h6>
	</div>
</div>


### Process packinglist (request object)
| Property                                | Type      | Description                      |
|-----------------------------------------|-----------|----------------------------------|
| `supplier_id`                           | `integer` | e.g. `2113`                      |
| `packinglist_number`                    | `string`  | e.g. `PB23323`                   |
| `store_id`                              | `integer` | e.g. `2`                         |
| `send_customer_messages`                | `boolean` | e.g. `false` defaults to `false` |
| `update_sales_order_status_if_possible` | `boolean` | e.g. `false` defaults to `false` |

### Process packinglist (response object)

| Property                                    | Type       | Nullable | Description                |
|---------------------------------------------|------------|----------|----------------------------|
| `error`                                     | `boolean`  | `false`  | e.g. `false`               |
| `error_message`                             | `null`     | `true`   |                            |
| `result.supplier_id`                        | `integer`  | `false`  | e.g. `2113`                |
| `result.packinglist_numbers`                | `string[]` | `false`  |                            |
| `result.articles`                           | `object[]` | `false`  |                            |
| `result.articles[].barcode`                 | `string`   | `false`  | e.g. `54423933323`         |
| `result.articles[].stock`                   | `integer`  | `false`  | e.g. `2`                   |
| `result.articles[].units_delivered`         | `integer`  | `false`  | e.g. `4`                   |
| `result.delivered_objects`                  | `object[]` | `false`  |                            |
| `result.delivered_objects[].customer_id`    | `?integer` | `false`  | e.g. `1006`                |
| `result.delivered_objects[].frame_number`   | `string`   | `false`  | e.g. `FR1443433`           |
| `result.delivered_objects[].object_id`      | `integer`  | `false`  | e.g. `10002`               |
| `result.delivered_objects[].sales_order_id` | `?integer` | `true`   |                            |
| `result.sales_orders`                       | `object[]` | `false`  |                            |
| `result.sales_orders[].barcode`             | `string`   | `false`  | e.g. `BARCODE2`            |
| `result.sales_orders[].item_status_id`      | `integer`  | `false`  | e.g. `3`                   |
| `result.sales_orders[].quantity`            | `integer`  | `false`  | e.g. `2`                   |
| `result.sales_orders[].sales_order_id`      | `integer`  | `false`  | e.g. `1002`                |
| `result.sales_orders[].status_id`           | `integer`  | `false`  | e.g. `2`                   |
| `result.notifications`                      | `object[]` | `false`  |                            |
| `result.notifications[].entity_id`          | `integer`  | `false`  | e.g. `1002`                |
| `result.notifications[].entity_type_id`     | `integer`  | `false`  | e.g. `7`                   |
| `result.notifications[].recipient`          | `string`   | `false`  | e.g. `test@mail.nl`        |
| `result.notifications[].status_text`        | `string`   | `false`  | e.g. `succesvol verzonden` |

> HTTP request

```http
POST /api/v1/supplier/packinglist/process-dropshipment.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json

{
    "supplier_id": 2113,
    "packinglist_number": "PB23323",
    "store_id": 2,
    "send_customer_messages": false,
    "update_sales_order_status_if_possible": false
}
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 1023
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "error": false,
    "error_message": null,
    "result": {
        "supplier_id": 2113
        "packinglist_numbers": [
            "PB23323"
        ],
        "articles": [
            {
                "barcode": "8723823933323",
                "stock": 2,
                "units_delivered": 4
            },
            {
                "barcode": "54423933323",
                "stock": 2,
                "units_delivered": 4
            }
        ],
        "delivered_objects": [
            {
                "customer_id": 1006,
                "frame_number": "",
                "object_id": 10001,
                "sales_order_id": 1000
            },
            {
                "customer_id": 1006,
                "frame_number": "FR1443433",
                "object_id": 10002,
                "sales_order_id": null
            }
        ],
        "sales_orders": [
            {
                "barcode": "BARCODE1",
                "item_status_id": 3,
                "quantity": 1,
                "sales_order_id": 1000,
                "status_id": 2
            },
            {
                "barcode": "BARCODE2",
                "item_status_id": 3,
                "quantity": 2,
                "sales_order_id": 1002,
                "status_id": 2
            }
        ],
        "notifications": [
            {
                "entity_id": 1000,
                "entity_type_id": 7,
                "recipient": "+3173030050",
                "status_text": "succesvol verzonden"
            },
            {
                "entity_id": 1002,
                "entity_type_id": 7,
                "recipient": "test@mail.nl",
                "status_text": "succesvol verzonden"
            }
        ]
    }
}
```
