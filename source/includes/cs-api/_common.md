# Common #

Access common data

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `common`

## Enums ##

Get a set of enums with identifiers and descriptions used in various APIs

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/common/enum.json</h6>
	</div>
</div>

### Types ###

| Subject                   | Description                                                                                 |
|---------------------------|---------------------------------------------------------------------------------------------|
| `sales_order_types`       | Sales order type descriptions                                                               |
| `sales_order_status`      | Sales order status descriptions                                                             |
| `sales_order_item_status` | Sales order item status descriptions                                                        |
| `cancellation_types`      | Cancellation reasons                                                                        |
| `pos_groups`              | POS / Sales group descriptions                                                              |
| `payment_methods`         | Payment method descriptions                                                                 |
| `delivery_methods`        | Delivery method descriptions                                                                |
| `vat_codes`               | VAT codes                                                                                   |
| `workshop_order_status`   | Workshop order status descriptions                                                          |
| `workshop_order_types`    | Workshop order type descriptions                                                            |
| `workshop_rates`          | Workshop rates descriptions                                                                 |
| `customer_types`          | Customer type descriptions                                                                  |
| `transaction_item_types`  | Transaction item type descriptions (item_type / row_type)                                   |
| `service_item_status`     | Status descriptions for object service items                                                |
| `entity_types`            | Entity types and descriptions, used as reference to an object in API requests and responses |
| `voucher_types`           | Voucher types and descriptions                                                              |
| `consignment_status`      | Object consignment type and descriptions                                                    |


> HTTP Request

```http
GET /api/v1/common/enum.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response (limited)

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 571
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

json
{
  "error": false,
  "error_message": null,
  "data": {
    "sales_order_types": [
      {
        "id": 0,
        "description": "Bestelling",
        "description_en": "Order"
      },
      {
        "id": 1,
        "description": "E-commerce",
        "description_en": "E-commerce"
      }
    ],
    "sales_order_status": [
      {
        "id": 2,
        "description": "In behandeling",
        "description_en": "Pending"
      },
      {
        "id": 8,
        "description": "Nog niet besteld",
        "description_en": "Not ordered"
      }
    ]
  }
}
```

## Employees ##

Get a list of employees associated with the account

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/common/employees.json</h6>
	</div>
</div>

### Properties ###

| Property                          | Type        | Description                                                                                                    |
|-----------------------------------|-------------|----------------------------------------------------------------------------------------------------------------|
| error                             | `boolean`   | e.g. `false`                                                                                                   |
| error_message                     | `?string`   | e.g. `Unauthorized`                                                                                            |
| data                              | `object[]`  | array of objects                                                                                               |
| data[].employee_id                | `integer`   | e.g. `4475`                                                                                                    |
| data[].employee_name              | `string`    | e.g. `John`                                                                                                    |
| data[].verification_hash          | `string`    | e.g. `8fa5a0b532ca29bdc06b97586993e04d8432ac37d9ed6632b63ccc967f28dbcb` sha256 hash mac with api-key as secret |
| data[].roles                      | `string[]`  | array of strings                                                                                               |
| data[].roles[]                    | `string`    | e.g. `employee`                                                                                                |
| data[].is_active                  | `boolean`   | e.g. `false`                                                                                                   |
| data[].is_default                 | `boolean`   | e.g. `false`                                                                                                   |
| data[].is_administrator           | `boolean`   | e.g. `false`                                                                                                   |
| data[].avatar                     | `?string`   | URL to avatar or null                                                                                          |
| data[].authorization[]            | `string[]`  | Array of authorizations e.g. `["MAY_ACCEPT_SALES_LEADS"]`                                                      |
| data[].authorizations_warehouse[] | `?string[]` | Array of authorizations for warehouse if warehouse account e.g. `["AUTH_ACCOUNTING"]`                          |

> HTTP Request

```http
GET /api/v1/common/employees.json HTTP/1.1
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
Content-length: 1220
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
      "employee_id": 44269,
      "employee_name": "John Doe",
      "verification_hash": "345ef8a695fded5cff8c2bfb83fa1bffc39f7bc9d13c589facac9ed2b41ebefe",
      "roles": [
        "employee"
      ],
      "is_active": true,
      "is_default": true,
      "is_administrator": false,
      "avatar": "https://s01.cyclesoftware.nl/app/cs/img/img_1_large_medewerker_44269.jpg",
      "authorizations": [
        "MAY_PERFORM_CYCLE_COUNT",
        "MAY_MODIFY_ARTICLE_PRICES",
        "MAY_REPLACE_ARTICLE",
        "MAY_MODIFY_ARTICLES",
        "MAY_IMPORT_SUPPLIER_ORDER",
        "MAY_SEND_SUPPLIER_ORDERS",
        "MAY_MANAGE_SUPPLIER_ORDERS",
        "MAY_DO_ANALYTICS"
      ]
    },
    {
      "employee_id": 1133,
      "employee_name": "Jane Doe",
      "verification_hash": "69baca4df93b1f213aff9d8582178ec6875da7d8c9bd030340d2de623aa19a69",
      "roles": [
        "mechanic"
      ],
      "is_active": true,
      "is_default": false,
      "is_administrator": false,
      "avatar": null,
      "authorizations": [
        "MAY_PERFORM_CYCLE_COUNT",
        "MAY_MODIFY_ARTICLE_PRICES",
        "MAY_REPLACE_ARTICLE"
      ]
    }
  ]
}
```

```php
<?php
// example on how to check personal code of employee

$api_key = 'your-api-key';
$code = '1234';
$hash = \hash_hmac('sha256', $code, $api_key);
if(\hash_equals('data[].verification_hash', $hash)){
   // code is correct
}
```


## Supplier list ##

Get a list of suppliers

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/common/suppliers.json</h6>
	</div>
</div>

### Properties ###

| Property                    | Type       | Description                                  |
|-----------------------------|------------|----------------------------------------------|
| `error`                     | `boolean`  | e.g. `false`                                 |
| `error_message`             | `?string`  | Error message if occured                     |
| `data`                      | `object[]` | Array of suppliers                           |
| `data[].type`               | `string`   | `supplier`, `bike-brand` or `moped-brand`    |
| `data[].supplier_id`        | `integer`  | Unique supplier ID `580`                     |
| `data[].supplier_name`      | `string`   | Name of supplier e.g. `Accell NL`            |
| `data[].parent_supplier_id` | `?integer` | Brands may be linked to a parent supplier-id |

> HTTP Request

```http
GET /api/v1/common/suppliers.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 331
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000
```

```json
{
  "error": false,
  "error_message": null,
  "data": [
    {
      "type": "supplier",
      "supplier_id": 122,
      "supplier_name": "Supplier A",
      "parent_supplier_id": null
    },
    {
      "type": "bike-brand",
      "supplier_id": 580,
      "supplier_name": "Brand one",
      "parent_supplier_id": 122
    }
  ]
}
```
