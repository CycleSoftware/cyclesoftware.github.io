# Stock locator #

Locate stock based on barcodes / article ids in associated accounts

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `platform` or `e-commerce`

## Properties ##

| Property                      | Type      | Nullable | Description                         |
|-------------------------------|-----------|----------|-------------------------------------|
| `error_message`               | `string`  | `true`   | Error message if occured            |
| `error`                       | `boolean` | `false`  | `true` if error occured             |
| `stores`                      | `array`   | `false`  | Array of store objects              |
| `stores[].store_id`           | `string`  | `false`  | Account ID in CS e.g.  `5185-1`     |
| `stores[].store_gln`          | `string`  | `false`  | GLN code `8718288145482`            |
| `stores[].store_name`         | `string`  | `false`  | Company name e.g. `CS-Unit test`    |
| `stores[].store_address`      | `string`  | `false`  | Company street e.g. `Kievitsven 22` |
| `stores[].store_postal_code`  | `string`  | `false`  | Company postal code e.g. `5249JJ`   |
| `stores[].store_phone_number` | `string`  | `false`  | Company phone number                |
| `stores[].store_country_code` | `string`  | `false`  | Company country code e.g. `NL`      |
| `stores[].store_email`        | `string`  | `false`  | e.g. `email5185@example.nl`         |
| `stores[].store_coordinates`  | `array`   | `false`  | array with `[latitude, longitude]`  |
| `stock`                       | `array`   | `false`  | List of stocked objects             |
| `stock[].store_id`            | `string`  | `false`  | Account ID in CS e.g. `1-1`         |
| `stock[].object_id`           | `integer` | `false`  | ID of object in account `18696`     |
| `stock[].barcode`             | `string`  | `false`  | Barcode of article `8717231204726`  |
| `stock[].article_id`          | `string`  | `false`  | Article number e.g. `30015`         |
| `stock[].brand_name`          | `string`  | `false`  | Brand name `Gazelle`                |
| `stock[].is_demo`             | `boolean` | `false`  | `true` if marked as demo bike       |

## Stores ##

Get a list of stores

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/stock-in-store-locator/stores.json</h6>
	</div>
</div>

> HTTP request

```http
GET /api/v1/stock-in-store-locator/stores.json HTTP/1.1
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
Content-length: 998

{
    "error_message": null,
    "error": false,
    "stores": [
        {
            "store_id": "1-1",
            "store_gln": "8718288145482",
            "store_name": "CycleSoftware",
            "store_address": "Raadhuisplein 1c",
            "store_postal_code": "5388GM",
            "store_phone_number": "0733030050",
            "store_country_code": "NL",
            "store_email": "email1@example.nl",
            "store_coordinates": [
                51.701163,
                5.5619904
            ]
        },
        {
            "store_id": "5185-1",
            "store_gln": "8718288145482",
            "store_name": "CS-Unit test",
            "store_address": "Kievitsven 22",
            "store_postal_code": "5249JJ",
            "store_phone_number": "",
            "store_country_code": "NL",
            "store_email": "email5185@example.nl",
            "store_coordinates": [
                51.7261667,
                5.3978953
            ]
        }
    ]
}
```

## Stock in store locator ##

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/stock-in-store-locator/stock.json</h6>
	</div>
</div>

> HTTP request

```http
POST /api/v1/stock-in-store-locator/stock.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8
Content-length: 65

[
	{
		"barcode": "8717144186799"
	},
	{
		"barcode": "8717231204726"
	}
]
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 989

{
    "error_message": null,
    "error": false,
    "stores": [
        {
            "store_id": "1-1",
            "store_gln": "8718288145482",
            "store_name": "CycleSoftware",
            "store_address": "Raadhuisplein 1c",
            "store_postal_code": "5388GM",
            "store_phone_number": "0733030050",
            "store_country_code": "NL",
            "store_email": "email1@example.nl",
            "store_coordinates": [
                51.701163,
                5.5619904
            ]
        },
        {
            "store_id": "5185-1",
            "store_gln": "8718288145482",
            "store_name": "CS-Unit test",
            "store_address": "Kievitsven 22",
            "store_postal_code": "5249JJ",
            "store_phone_number": "",
            "store_country_code": "NL",
            "store_email": "email5185@example.nl",
            "store_coordinates": [
                51.7261667,
                5.3978953
            ]
        }
    ],
    "stock": [
        {
            "store_id": "5185-1",
            "object_id": 144922,
            "barcode": "8717144186799",
            "article_id": "03505002",
            "brand_name": "Sparta",
            "is_demo": false
        },
        {
            "store_id": "1-1",
            "object_id": 18695,
            "barcode": "8717231204726",
            "article_id": "30015",
            "brand_name": "Gazelle",
            "is_demo": false
        },
        {
            "store_id": "1-1",
            "object_id": 18696,
            "barcode": "8717231204726",
            "article_id": "30015",
            "brand_name": "Gazelle",
            "is_demo": false
        }
    ]
}
```
