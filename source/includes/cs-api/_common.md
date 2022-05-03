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

| Subject                 | Description                                               |
|-------------------------|-----------------------------------------------------------|
| sales_order_types       | Sales order type descriptions                             |
| sales_order_status      | Sales order status descriptions                           |
| sales_order_item_status | Sales order item status descriptions                      |
| cancellation_types      | Cancellation reasons                                      |
| pos_groups              | POS / Sales group descriptions                            |
| payment_methods         | Payment method descriptions                               |
| delivery_methods        | Delivery method descriptions                              |
| vat_codes               | VAT codes                                                 |
| workshop_order_status   | Workshop order status descriptions                        |
| customer_types          | Customer type descriptions                                |
| transaction_item_types  | Transaction item type descriptions (item_type / row_type) |


> HTTP Request

```http
GET /api/v1/common/enum.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip,deflate
Accept: application/json
Content-type: application/json; charset=utf-8
```

> HTTP Response (limited)

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 571
```

```json
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

| Property                 | Type      | Nullable | Description                                                                                                    |
|--------------------------|-----------|----------|----------------------------------------------------------------------------------------------------------------|
| error                    | `boolean` | `false`  | e.g. `false`                                                                                                   |
| error_message            | `string`  | `true`   | e.g. `Unauthorized`                                                                                            |
| data                     | `array`   | `false`  | array of objects                                                                                               |
| data[].employee_id       | `integer` | `false`  | e.g. `4475`                                                                                                    |
| data[].employee_name     | `string`  | `false`  | e.g. `John`                                                                                                    |
| data[].verification_hash | `string`  | `false`  | e.g. `8fa5a0b532ca29bdc06b97586993e04d8432ac37d9ed6632b63ccc967f28dbcb` sha256 hash mac with api-key as secret |
| data[].roles             | `array`   | `false`  | array of strings                                                                                               |
| data[].roles[]           | `string`  | `false`  | e.g. `employee`                                                                                                |
| data[].is_active         | `boolean` | `false`  | e.g. `false`                                                                                                   |
| data[].is_default        | `boolean` | `false`  | e.g. `false`                                                                                                   |
| data[].is_administrator  | `boolean` | `false`  | e.g. `false`                                                                                                   |
| data[].avatar            | `string`  | `true`   | URL to avatar or null                                                                                          |
| data[].authorizations    | `array`   | `false`  | array of strings                                                                                               |
| data[].authorizations[]  | `string`  | `false`  | e.g. `MAY_ACCEPT_SALES_LEADS`                                                                                  |

> HTTP Request

```http
GET /api/v1/common/employees.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip,deflate
Accept: application/json
Content-type: application/json; charset=utf-8
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 1220
```

```json
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
