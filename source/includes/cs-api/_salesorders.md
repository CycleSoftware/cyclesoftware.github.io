# Sales orders #

For create and update of sales orders see the E-commerce documentation section.

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `e-commerce`

## Update sales order store ##

Update the store of a sales order with the possibility to change the delivery type and address. This API call may only
be used if your account has multiple stores. If no mode is specified in the items array objects the default mode will be used.

| URL parameter     | Type      | Description                                                                                         |
|-------------------|-----------|-----------------------------------------------------------------------------------------------------|
| `:sales_order_id` | `integer` | Sales order id also referred to as `order_id` in SOAP APIs <i class="label label-info">required</i> |

### HTTP request example ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/sales/orders/:sales_order_id/update-store.json</h6>
	</div>
</div>

### Request properties ###

| Property                                    | Type      | Nullable | Description                                                                                                           |
|---------------------------------------------|-----------|----------|-----------------------------------------------------------------------------------------------------------------------|
| `to_store_id`                               | `integer` | `false`  | The new store id e.g. `2`                                                                                             |
| `default_mode`                              | `integer` | `false`  | Default transfer mode `2` (see common enum api `sales_order_store_transfer_modes`)                                    |
| `new_delivery_method_id`                    | `integer` | `true`   | New delivery method `3` (see common enum api  `delivery_methods`)                                                     |
| `new_delivery_address`                      | `object`  | `true`   | New delivery address for the sales order (`null` if not changed or required)                                          |
| `new_delivery_address.is_business_address`  | `bool`    | `false`  | `true` if business address                                                                                            |
| `new_delivery_address.company_name`         | `string`  | `true`   | Company name or `null`                                                                                                |
| `new_delivery_address.name`                 | `string`  | `false`  | The name of the address                                                                                               |
| `new_delivery_address.street`               | `string`  | `false`  | Street name of the address                                                                                            |
| `new_delivery_address.house_number`         | `string`  | `false`  | House number of the address                                                                                           |
| `new_delivery_address.house_number_postfix` | `string`  | `false`  | House number postfix of the address                                                                                   |
| `new_delivery_address.postal_code`          | `string`  | `false`  | Postal code of the address                                                                                            |
| `new_delivery_address.city`                 | `string`  | `false`  | City of the address                                                                                                   |
| `new_delivery_address.country_code`         | `string`  | `false`  | Country_code of the address                                                                                           |
| `new_delivery_address.phone_number`         | `string`  | `false`  | Phone_number of the address                                                                                           |
| `new_delivery_address.email`                | `string`  | `false`  | E-mail of the address com`                                                                                            |
| `new_delivery_address.notes`                | `string`  | `false`  | Notes of the address                                                                                                  |
| `items`                                     | `array`   | `false`  | List of sales order items and associated transfer mode                                                                |
| `items[].item_id`                           | `integer` | `false`  | The sales order item id, also referred to as order_item_line_id in e-commerce APIs                                    |
| `items[].mode`                              | `integer` | `true`   | Specify the transfer mode for this specific sales order item (see common enum api `sales_order_store_transfer_modes`) |

### Response properties ###

| Property                       | Type      | Nullable | Description                                                            |
|--------------------------------|-----------|----------|------------------------------------------------------------------------|
| `error`                        | `boolean` | `false`  | `true` if an error occcured                                            |
| `error_message`                | `string`  | `true`   | The error message if `error` is `true`                                 |
| `created_store_order_id`       | `integer` | `true`   | The internal delivery store order id that was created `45287`          |
| `affected_supplier_order_ids`  | `array`   | `false`  | List of supplier order ids that may have a new store                   |
| `cancelled_store_order_ids`    | `array`   | `false`  | List of store orders which were cancelled                              |
| `cancelled_supplier_order_ids` | `array`   | `false`  | List of supplier orders which were cancelled                           |
| `updated_outbound_order_ids`   | `array`   | `true`   | List of outbound order ids which were cancelled (if warehouse account) |

> HTTP Request

```http
POST /api/v1/sales/orders/102323/update-store.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept: application/json
Accept-encoding: gzip
Content-type: application/json; charset=utf-8
Content-Length: 688

{
    "to_store_id": 2,
    "default_mode": 2,
    "new_delivery_method_id": 3,
    "new_delivery_address": {
        "address_type_id": "1",
        "is_business_address": "0",
        "company_name": "",
        "name": "Name 1",
        "street": "Streetname",
        "house_number": "1",
        "house_number_postfix": "a",
        "postal_code": "1000AA",
        "city": "Amsterdam",
        "country_code": "NL",
        "phone_number": "073031111",
        "email": "test@test.com",
        "notes": "Some note"
    },
    "items": [
        {
            "item_id": 1,
            "mode": 1
        },
        {
            "item_id": 2,
            "mode": 1
        }
    ]
}
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 45
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "error": false,
    "error_message": null,
    "created_store_order_id": 45287,
    "affected_supplier_order_ids": [
        1481,
        20000
    ],
    "cancelled_store_order_ids": [
        3333,
        4444
    ],
    "cancelled_supplier_order_ids": [
        102020,
        102021
    ],
    "updated_outbound_order_ids": [
        32323,
        32324
    ]
}
```

## Cancel sales order ##

Mark a sales order as cancelled. An order may only be cancelled if there is no payment amount left and the sales orders is not invoiced.

| URL parameter     | Type      | Description                                                                                         |
|-------------------|-----------|-----------------------------------------------------------------------------------------------------|
| `:sales_order_id` | `integer` | Sales order id also referred to as `order_id` in SOAP APIs <i class="label label-info">required</i> |

| GET parameter           | Type      | Description                                                                      |
|-------------------------|-----------|----------------------------------------------------------------------------------|
| `:cancellation_type_id` | `integer` | Cancellation type ID see common api `cancellation_types` e.g. `1`                |
| `:delete_exchange`      | `bool`    | if `true` the exchange objects in the order will be deleted. Defaults to `false` |

### HTTP request example ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/sales/orders/:sales_order_id/cancel.json?cancellation_type_id=:cancellation_type_id&delete_exchange=:delete_exchange</h6>
	</div>
</div>


> HTTP Request

```http
POST /api/v1/sales/orders/121212/cancel.json?cancellation_type_id=1&delete_exchange=true HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 45

{
  "error": false,
  "error_message": null
}
```
