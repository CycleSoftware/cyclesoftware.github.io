# Outbound orders #

Outbound orders related APIs

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `warehouse`


## Open order items ##

Get a list of open outbound order items: `quantity shipped < quantity`

| GET parameter | Type      | Description     |
|---------------|-----------|-----------------|
| `:page`       | `integer` | Pagination page |


### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/warehouse/outbound/order/open-orders.json?page=:page</h6>
	</div>
</div>


| Property                          | Type       | Description                                      |
|-----------------------------------|------------|--------------------------------------------------|
| `error`                           | `boolean`  | `false` if no error occured                      |
| `error_message`                   | `?string`  | Error message if present                         |
| `data`                            | `object[]` | Array of OBO items                               |
| `data[].dealer_id`                | `integer`  | The dealer ID e.g. `99`                          |
| `data[].outbound_order_id`        | `integer`  | Outbound order ID e.g. `204915`                  |
| `data[].outbound_order_item_id`   | `integer`  | Outbound order item ID  e.g. `307229`            |
| `data[].created_at`               | `datetime` | Date time created `2019-08-15 12:48:10`          |
| `data[].ecommerce_reference_id`   | `string`   | Reference ID                                     |
| `data[].ecommerce_reference_text` | `string`   | Reference Text                                   |
| `data[].barcode`                  | `string`   | Barcode e.g. `8717231260616`                     |
| `data[].description`              | `string`   | Description e.g. `Esprit C3 H 59 T3`             |
| `data[].quantity`                 | `integer`  | Quantity of item e.g. `1`                        |
| `data[].quantity_claimed`         | `integer`  | Quantity claimed e.g. `0`                        |
| `data[].quantity_shipped`         | `integer`  | Quantity shipped e.g. `0`                        |
| `data[].reference`                | `string`   | Reference to POS order                           |
| `data[].is_sold_to_customer`      | `boolean`  | `true` if sold to customer                       |
| `data[].is_blocked_for_claiming`  | `boolean`  | `true` if item is blocked for claiming           |
| `data[].is_pooled_within_stores`  | `boolean`  | `true` if item is sourced within stores          |
| `pagination.page`                 | `integer`  | Pagination page `1`                              |
| `pagination.count`                | `integer`  | Count result items `262`                         |
| `pagination.has_next_page`        | `boolean`  | If `true` call endpoint again with `page=page+1` |



> HTTP Request

```http
GET /api/v1/warehouse/outbound/order/open-orders.json?page=1 HTTP/1.1
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
Content-length: 1441
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
            "dealer_id": 4807,
            "outbound_order_id": 225,
            "outbound_order_item_id": 277,
            "created_at": "2014-01-03 15:05:16",
            "ecommerce_reference_id": "FV_121212",
            "ecommerce_reference_text": "FV_121212",
            "barcode": "8717231228326",
            "description": "Gazelle MS GRACE Dames Black 2014 49",
            "quantity": 1,
            "quantity_claimed": 0,
            "quantity_shipped": 0,
            "reference": "POS12121076",
            "is_sold_to_customer": true,
            "is_blocked_for_claiming": false,
            "is_pooled_within_stores": false
        },
        {
            "dealer_id": 4807,
            "outbound_order_id": 231,
            "outbound_order_item_id": 283,
            "created_at": "2014-01-07 15:49:15",
            "ecommerce_reference_id": "",
            "ecommerce_reference_text": "",
            "barcode": "8713568224574",
            "description": "Batavus",
            "quantity": 1,
            "quantity_claimed": 0,
            "quantity_shipped": 0,
            "reference": "F.1080",
            "is_sold_to_customer": true,
            "is_blocked_for_claiming": false,
            "is_pooled_within_stores": false
        },
    ],
    "pagination": {
        "page": 1,
        "count": 2,
        "has_next_page": false
    }
}
```


## Convert pool to regular ##

Convert a POOL order to a regular order.

| URL parameter        | Type      | Description                                                |
|----------------------|-----------|------------------------------------------------------------|
| `:outbound_order_id` | `integer` | Outbound order id <i class="label label-info">required</i> |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/warehouse/outbound/order/:outbound_order_id/pool-to-regular.json</h6>
	</div>
</div>


> HTTP Request 

```http
POST /api/v1/warehouse/outbound/order/1013123/pool-to-regular.json HTTP/1.1
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
Content-length: 722
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
  "error": false,
  "error_message": null
}
```


## Cancel order ##

Cancel an outbound order

| URL parameter        | Type      | Description                                                |
|----------------------|-----------|------------------------------------------------------------|
| `:outbound_order_id` | `integer` | Outbound order id <i class="label label-info">required</i> |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/warehouse/outbound/order/:outbound_order_id/cancel.json</h6>
	</div>
</div>


> HTTP Request

```http
POST /api/v1/warehouse/outbound/order/1013123/cancel.json HTTP/1.1
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
Content-length: 269
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "error": false,
    "error_message": null,
    "result": [
        {
            "outbound_order_item_id": 111,
            "unclaimed_stock": 2
        },
        {
            "outbound_order_item_id": 333,
            "unclaimed_stock": 3
        }
    ]
}
```
