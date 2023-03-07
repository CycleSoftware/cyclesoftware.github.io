# Repair objects #

Read, create or update repair objects for a customer

***Scope(s)***

- `resources`

## Repair object (object)

| **Property**             | **Type**                        | **Modify**                 | **Description**                                                                            |
|--------------------------|---------------------------------|----------------------------|--------------------------------------------------------------------------------------------|
| `customer_id`            | `integer`                       | `readonly`                 | Customer ID of owner e.g. `6`                                                              |
| `object_id`              | `integer`                       | `readonly`                 | ID of the object e.g. `208410`                                                             |
| `object_barcode`         | `string`                        | <code>PUT&#124;POST</code> | e.g. `object_barcode`                                                                      |
| `is_active`              | `boolean`                       | <code>PUT&#124;POST</code> | Whether this object is still owned by customer e.g. `true`                                 |
| `object_type_name`       | `string`                        | <code>PUT&#124;POST</code> | e.g. `fiets`                                                                               |
| `category`               | `string`                        | <code>PUT&#124;POST</code> | Category name e.g. `Racefietsen`                                                           |
| `brand`                  | `string`                        | <code>PUT&#124;POST</code> | Brand name e.g. `BrandName`                                                                |
| `model`                  | `string`                        | <code>PUT&#124;POST</code> | Model name e.g. `ModelName`                                                                |
| `model_year`             | `string`                        | <code>PUT&#124;POST</code> | Model year e.g. `2017`                                                                     |
| `color`                  | `string`                        | <code>PUT&#124;POST</code> | Color of object e.g. `Black`                                                               |
| `variant`                | `string`                        | <code>PUT&#124;POST</code> | Variant name e.g. `Heren`                                                                  |
| `phone_number_id`        | `string`                        | <code>PUT&#124;POST</code> | Phone number ID for communication e.g. `12345`                                             |
| `license_plate`          | `string`                        | <code>PUT&#124;POST</code> | License plate number e.g. `xx-zz-yy`                                                       |
| `km_mileage`             | `string`                        | <code>PUT&#124;POST</code> | Kilometer age e.g. `200`                                                                   |
| `frame_id`               | `string`                        | <code>PUT&#124;POST</code> | Frame number e.g. `frame_id`                                                               |
| `chip_id`                | `string`                        | <code>PUT&#124;POST</code> | Chip number e.g. `chip_id`                                                                 |
| `key_id`                 | `string`                        | <code>PUT&#124;POST</code> | Key number e.g. `key_id`                                                                   |
| `engine_id`              | `string`                        | <code>PUT&#124;POST</code> | Engine number e.g. `engine_id`                                                             |
| `battery_id`             | `string`                        | <code>PUT&#124;POST</code> | Battery number e.g. `1234`                                                                 |
| `lock_id`                | `string`                        | <code>PUT&#124;POST</code> | Lock number e.g. `1234`                                                                    |
| `workshop_rate_id`       | `integer`                       | <code>PUT&#124;POST</code> | See common API `workshop_rates` e.g. `1`                                                   |
| `service_level_id`       | `integer`                       | <code>PUT&#124;POST</code> | Service level ID e.g. `0`                                                                  |
| `images`                 | `array`                         | `readonly`                 | Array of images                                                                            |
| `images[].date_modified` | <code>datetime&#124;null</code> | `readonly`                 | Modification date e.g. `2016-05-24 11:15:02`                                               |
| `images[].url_thumb`     | `string`                        | `readonly`                 | URL to thumbnail e.g. `https://s01.cyclesoftware.nl/app/img/artPic_public_T_1317089.jpg`   |
| `images[].url_large`     | `string`                        | `readonly`                 | URL to large image e.g. `https://s01.cyclesoftware.nl/app/img/artPic_public_L_1317089.jpg` |


## List repair objects 

Get a list of repair objects for a customer

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v1/customers/:customer_id/objects.json</h6>
    </div>
</div>

| **URI parameter** | **Type** | **Description**                            |
|-------------------|----------|--------------------------------------------|
| `customer_id`     | `int`    | Customer ID to get objects for e.g. `1006` |


> HTTP request

```http
GET /api/v1/customers/1006/objects.json HTTP/1.1
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
Content-length: 1676

[
    {
        "customer_id": 1006,
        "object_id": 1004,
        "object_barcode": "",
        "is_active": true,
        "object_type_name": "fiets",
        "category": "Hybride fietsen",
        "brand": "Batavus",
        "model": "Apache Deluxe",
        "model_year": "",
        "color": "Scumzilver",
        "variant": "Dames",
        "phone_number_id": "mob",
        "license_plate": "",
        "km_mileage": "0",
        "frame_id": "",
        "chip_id": "",
        "key_id": "",
        "engine_id": "",
        "battery_id": "",
        "lock_id": "",
        "workshop_rate_id": 1,
        "service_level_id": 0,
        "images": [
            {
                "date_modified": "2016-05-24 11:15:02",
                "url_thumb": "https://s01.cyclesoftware.nl/app/img/artPic_public_T_1317089.jpg",
                "url_large": "https://s01.cyclesoftware.nl/app/img/artPic_public_L_1317089.jpg"
            }
        ]
    },
    {
        "customer_id": 1006,
        "object_id": 208410,
        "object_barcode": "object_barcode",
        "is_active": true,
        "object_type_name": "fiets",
        "category": "Racefietsen",
        "brand": "brand",
        "model": "model",
        "model_year": "2017",
        "color": "color",
        "variant": "Heren",
        "phone_number_id": "12345",
        "license_plate": "license_plate",
        "km_mileage": "200",
        "frame_id": "frame_id",
        "chip_id": "chip_id",
        "key_id": "key_id",
        "engine_id": "engine_id",
        "battery_id": "1234",
        "lock_id": "lock_id",
        "workshop_rate_id": 1,
        "service_level_id": 0,
        "images": []
    }
]
```

## Get repair object

Get a repair object

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v1/customers/:customer_id/objects/:object_id.json</h6>
    </div>
</div>

| **URI parameter** | **Type** | **Description**              |
|-------------------|----------|------------------------------|
| `customer_id`     | `int`    | Customer ID e.g. `1006`      |
| `object_id`       | `int`    | Repair object ID e.g. `1004` |



> HTTP request

```http
GET /api/v1/customers/1006/objects/1004.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic
Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8

```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 827

{
    "customer_id": 1006,
    "object_id": 1004,
    "object_barcode": "",
    "is_active": true,
    "object_type_name": "fiets",
    "category": "Hybride fietsen",
    "brand": "Batavus",
    "model": "Apache Deluxe",
    "model_year": "",
    "color": "Scumzilver",
    "variant": "Dames",
    "phone_number_id": "mob",
    "license_plate": "",
    "km_mileage": "0",
    "frame_id": "",
    "chip_id": "",
    "key_id": "",
    "engine_id": "",
    "battery_id": "",
    "lock_id": "",
    "workshop_rate_id": 1,
    "service_level_id": 0,
    "images": [
        {
            "date_modified": "2016-05-24 11:15:02",
            "url_thumb": "https://s01.cyclesoftware.nl/app/img/artPic_public_T_1317089.jpg",
            "url_large": "https://s01.cyclesoftware.nl/app/img/artPic_public_L_1317089.jpg"
        }
    ]
}
```


## Create repair object

Create a repair object for a customer

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">POST</i>
        <h6>/api/v1/customers/:customer_id/objects.json</h6>
    </div>
</div>

| **URI parameter** | **Type** | **Description**       |
|-------------------|----------|-----------------------|
| `customer_id`     | `int`    | Customer ID e.g. `24` |


> HTTP request

```http
POST /api/v1/customers/24/objects.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic
Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8
Content-length: 620

{
    "object_id": 208694,
    "object_barcode": "object_barcode",
    "is_active": true,
    "object_type_name": "fiets",
    "category": "Racefietsen",
    "brand": "brand",
    "model": "model",
    "model_year": "2017",
    "color": "color",
    "variant": "Heren",
    "phone_number_id": "12345",
    "license_plate": "license_plate",
    "km_mileage": "200",
    "frame_id": "frame_id",
    "chip_id": "chip_id",
    "key_id": "key_id",
    "engine_id": "engine_id",
    "battery_id": "1234",
    "lock_id": "lock_id",
    "workshop_rate_id": 1,
    "service_level_id": 0
}
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 620

{
    "customer_id": 24,
    "object_id": 208694,
    "object_barcode": "object_barcode",
    "is_active": true,
    "object_type_name": "fiets",
    "category": "Racefietsen",
    "brand": "brand",
    "model": "model",
    "model_year": "2017",
    "color": "color",
    "variant": "Heren",
    "phone_number_id": "12345",
    "license_plate": "license_plate",
    "km_mileage": "200",
    "frame_id": "frame_id",
    "chip_id": "chip_id",
    "key_id": "key_id",
    "engine_id": "engine_id",
    "battery_id": "1234",
    "lock_id": "lock_id",
    "workshop_rate_id": 1,
    "service_level_id": 0,
    "images": []
}
```

## Update repair object

Update a repair object

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">PUT</i>
        <h6>/api/v1/customers/:customer_id/objects/:repair_object_id.json</h6>
    </div>
</div>

| **URI parameter**  | **Type** | **Description**                |
|--------------------|----------|--------------------------------|
| `customer_id`      | `int`    | Customer ID e.g. `1900`        |
| `repair_object_id` | `int`    | Repair Object ID e.g. `152614` |


> HTTP request

```http
PUT /api/v1/customers/1900/objects/152614.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic
Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8
Content-length: 853

{
    "object_barcode": "barcode_object",
    "is_active": true,
    "category": "Mountainbikes",
    "brand": "Cube",
    "model": "6407189221756",
    "model_year": "2023",
    "color": "Carbon´n´blue",
    "variant": "Dames",
    "phone_number_id": "mob"
}
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 853

{
    "customer_id": 1900,
    "object_id": 152614,
    "object_barcode": "barcode_object",
    "is_active": true,
    "object_type_name": "fiets",
    "category": "Mountainbikes",
    "brand": "Cube",
    "model": "6407189221756",
    "model_year": "2023",
    "color": "Carbon´n´blue",
    "variant": "Dames",
    "phone_number_id": "mob",
    "license_plate": "",
    "km_mileage": "0",
    "frame_id": "",
    "chip_id": "",
    "key_id": "",
    "engine_id": "",
    "battery_id": "",
    "lock_id": "",
    "workshop_rate_id": 1,
    "service_level_id": 1,
    "images": [
        {
            "date_modified": "2014-12-19 08:35:58",
            "url_thumb": "https://s01.cyclesoftware.nl/app/img/artPic_public_T_1215427.jpg",
            "url_large": "https://s01.cyclesoftware.nl/app/img/artPic_public_L_1215427.jpg"
        }
    ]
}
```
