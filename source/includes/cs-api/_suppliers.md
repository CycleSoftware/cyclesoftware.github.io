# Suppliers #

Create and send supplier orders

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `e-commerce`


### Supplier order properties

Properties used in create, get and send endpoints.

| Property                          | Type       | Nullable | Create | Description                                                 |
|-----------------------------------|------------|----------|--------|-------------------------------------------------------------|
| `supplier_order_id`               | `integer`  | `false`  |        | Supplier order ID `2222`                                    |
| `supplier_id`                     | `integer`  | `false`  | X      | Supplier ID see common suppliers endpoint e.g. `2113`       |
| `store_id`                        | `integer`  | `false`  | X      | Store ID within account e.g. `2`                            |
| `order_type_id`                   | `integer`  | `false`  |        | Order type see common enum supplier_order_types e.g. `1`    |
| `status_id`                       | `integer`  | `false`  |        | Order status see common enum supplier_order_status e.g. `0` |
| `supplier_comment`                | `string`   | `false`  |        | Comment given by supplier e.g. `Some text`                  |
| `supplier_reference`              | `string`   | `false`  |        | Reference from supplier `ref-from-supplier`                 |
| `created_at`                      | `datetime` | `false`  |        | Creation date `2022-01-12 12:30:30`                         |
| `items`                           | `array`    | `false`  |        | Array of order items                                        |
| `items[].supplier_order_item_id`  | `integer`  | `false`  |        | Item ID `10012`                                             |
| `items[].item_type_id`            | `integer`  | `false`  |        | Item type see common enum transaction_item_types e.g. `1`   |
| `items[].article_id`              | `string`   | `false`  | X      | Article Number. `ART2`                                      |
| `items[].barcode`                 | `string`   | `false`  | X      | Barcode e.g. `BARCODE2`                                     |
| `items[].quantity`                | `integer`  | `false`  | X      | Quantity ordered e.g. `2`                                   |
| `items[].quantity_delivered`      | `integer`  | `false`  |        | Quantity delivered e.g. `0`                                 |
| `items[].quantity_open`           | `integer`  | `false`  |        | Quantity open (not delivered) e.g. `2`                      |
| `items[].supplier_delivery_date`  | `date`     | `false`  |        | Delivery date given by supplier e.g. `2022-01-20`           |
| `items[].supplier_item_reference` | `string`   | `false`  |        | Reference item from supplier e.g. `ref-item-1`              |


## Create supplier order

Creates a supplier order. To actually dispatch and send the supplier order to the supplier call the send endpoint with the obtained supplier order ID.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/supplier/order/</h6>
	</div>
</div>

> HTTP request

```http
POST /api/v1/supplier/order/ HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8
Content-length: 299

{
    "supplier_id": 2113,
    "store_id": 2,
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
Content-length: 989

{
    "supplier_order_id": 2222,
    "supplier_id": 2113,
    "store_id": 2,
    "order_type_id": 1,
    "status_id": 0,
    "supplier_comment": "Some text",
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
Content-type: application/json; charset=utf-8
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 989

{
    "supplier_order_id": 2222,
    "supplier_id": 2113,
    "store_id": 2,
    "order_type_id": 1,
    "status_id": 0,
    "supplier_comment": "Some text",
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
Content-type: application/json; charset=utf-8
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 989

{
    "supplier_order_id": 2222,
    "supplier_id": 2113,
    "store_id": 2,
    "order_type_id": 1,
    "status_id": 1,
    "supplier_comment": "Some text",
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

{
    "error": true,
    "error_message": "Error given by supplier"
}
```
