# Stock objects #

## Stock object batch updates (beta) ##

Apply batch updates to stock objects. Be aware that during the beta-phase the properties may change.
You can only update stock objects which are not sold and are not used.

***Authentication mechanism***

- Basic HTTP Authentication
- Scopes: `resources`

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">PATCH</i>
		<h6>/api/beta/stock-objects/batch/update.json</h6>
	</div>
</div>

### Request properties

| Property                                | Type       | Required | Description                                                                                                                                                      |
|-----------------------------------------|------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `updates`                               | `object[]` | `true`   | Array with data objects, maximum of 150 items                                                                                                                    |

### Request properties

| Property                            | Type        | Nullable | Omittable | Description                                                    |
|-------------------------------------|-------------|----------|-----------|----------------------------------------------------------------|
| `updates`                           | `object[]`  | `false`  |           | Array of updates                                               |
| `updates[].filter`                  | `object`    | `false`  | `Yes`     | Filter that contains information about which objects to update |
| `updates[].filter.barcode`          | `string`    | `false`  | `Yes`     | Barcode of stock object to update                              |
| `updates[].filter.stock_object_ids` | `integer[]` | `false`  | `Yes`     | List of stock object ids to update                             |
| `updates[].....                     | `@todo[]`   | `@todo`  | `@todo`   | @Todo                                                          |


### Result properties

| Property                                      | Type       | Nullable | Omittable | Description                                                                                                                                                                                                                                                                                  |
|-----------------------------------------------|------------|----------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `results`                                     | `object[]` | `false`  |           | Array of result objects                                                                                                                                                                                                                                                                      |
| `results[].result`                            | `string`   | `false`  |           | Result status `success` (all fields updated),  `partial` (not all fields could be updated see `results[].skipped_fields`, `success_with_warnings` (all fields updated with some warnings, see `results[].warnings`), `error` (article not updated or created, see `results[].error.message`) |
| `results[].object`                            | `object`   | `false`  | `Yes`     | Object with resulting stock object details, omitted when an error occurs                                                                                                                                                                                                                     |
| `results[].stock_object_id`                   | `integer`  | `false`  | `Yes`     | If present the update is based on filter.stock_object_ids and this field is the stock-object affected e.g. `26042`                                                                                                                                                                           |
| `results[].barcode`                           | `integer`  | `false`  | `Yes`     | If present the update is based on filter.barcode e.g. `26042`                                                                                                                                                                                                                                |
| `results[].result`                            | `string`   | `false`  |           | Result status `success` (all fields updated),  `partial` (not all fields could be updated see `results[].skipped_fields`, `success_with_warnings` (all fields updated with some warnings, see `results[].warnings`), `error` (article not updated or created, see `results[].error.message`) |
| `results[].object.stock_object_id`            | `integer`  | `false`  |           | Stock object ID e.g. `26042`                                                                                                                                                                                                                                                                 |
| `results[].object.is_reserved`                | `boolean`  | `false`  |           | `true` if object is reserved e.g. `false`                                                                                                                                                                                                                                                    |
| `results[].object.is_demo`                    | `boolean`  | `false`  |           | `true` if object is demo e.g. `false`                                                                                                                                                                                                                                                        |
| `results[].object.object_reference`           | `string`   | `false`  |           | Object reference e.g. `F23322332`                                                                                                                                                                                                                                                            |
| `results[].object.barcode`                    | `string`   | `false`  |           | Barcode of object e.g. `878734843384`                                                                                                                                                                                                                                                        |
| `results[].object.article_id`                 | `string`   | `false`  |           | Article ID of object e.g. `0298`                                                                                                                                                                                                                                                             |
| `results[].object.brand_name`                 | `string`   | `false`  |           | Brand name of object e.g. `Batavus`                                                                                                                                                                                                                                                          |
| `results[].object.brand_id`                   | `integer`  | `false`  |           | Brand ID of object e.g. `1759`                                                                                                                                                                                                                                                               |
| `results[].object.model_name`                 | `string`   | `false`  |           | Model name of object e.g. `New model name`                                                                                                                                                                                                                                                   |
| `results[].object.article_main_group`         | `integer`  | `false`  |           | Main article group ID e.g. `1` - should always be `1` for bikes (@todo codelist)                                                                                                                                                                                                             |
| `results[].object.article_group`              | `string`   | `false`  |           | Article group ID e.g. `A` (@todo codelist)                                                                                                                                                                                                                                                   |
| `results[].object.article_sub_group`          | `integer`  | `false`  |           | Sub article group ID e.g. `1` (@todo codelist)                                                                                                                                                                                                                                               |
| `results[].object.frame_type`                 | `string`   | `false`  |           | Frametype of object e.g. `WOMEN` (if language is nl_NL this field will be in Dutch)                                                                                                                                                                                                          |
| `results[].object.model_year`                 | `integer`  | `false`  |           | Model year of object  e.g. `2025`                                                                                                                                                                                                                                                            |
| `results[].object.frame_height`               | `integer`  | `false`  |           | Frame height in CM e.g. `53`                                                                                                                                                                                                                                                                 |
| `results[].object.frame_size_supplier`        | `string`   | `false`  |           | Frame size description e.g. `M`                                                                                                                                                                                                                                                              |
| `results[].object.wheel_size`                 | `integer`  | `false`  |           | Wheel size in inch e.g. `28`                                                                                                                                                                                                                                                                 |
| `results[].object.customer_group`             | `string`   | `false`  |           | Customer group e.g. `MEN`  (if language is nl_NL this field will be in Dutch)                                                                                                                                                                                                                |
| `results[].object.frame_material`             | `string`   | `false`  |           | Frame material e.g. `CARBON` (if language is nl_NL this field will be in Dutch)                                                                                                                                                                                                              |
| `results[].object.color`                      | `string`   | `false`  |           | Color description e.g. `Scumzilver`                                                                                                                                                                                                                                                          |
| `results[].object.primary_color`              | `string`   | `false`  |           | Primary color e.g. `BLACK` (if language is nl_NL this field will be in Dutch)                                                                                                                                                                                                                |
| `results[].object.secondary_color`            | `string`   | `false`  |           | Secondary color e.g. `BLACK` (if language is nl_NL this field will be in Dutch)                                                                                                                                                                                                              |
| `results[].object.type_brake_system_front`    | `string`   | `false`  |           | Type brake system front e.g. `` (@todo-- code list)                                                                                                                                                                                                                                          |
| `results[].object.brand_brake_system_front`   | `string`   | `false`  |           | Brand brake system front e.g. `SRAM` (@todo-- code list)                                                                                                                                                                                                                                     |
| `results[].object.model_brake_system_front`   | `string`   | `false`  |           | Model brake system front e.g. `Modelname`                                                                                                                                                                                                                                                    |
| `results[].object.type_brake_system_rear`     | `string`   | `false`  |           | Type brake system rear e.g. ``   (@todo-- code list)                                                                                                                                                                                                                                         |
| `results[].object.brand_brake_system_rear`    | `string`   | `false`  |           | Brand brake system rear e.g. `SRAM` (@todo-- code list)                                                                                                                                                                                                                                      |
| `results[].object.model_brake_system_rear`    | `string`   | `false`  |           | Model brake system rear e.g. `Modelname`                                                                                                                                                                                                                                                     |
| `results[].object.type_gear_system`           | `string`   | `false`  |           | Type gear system e.g. `` (@todo-- code list)                                                                                                                                                                                                                                                 |
| `results[].object.brand_gear_system`          | `string`   | `false`  |           | Brand gear system e.g. `SRAM` (@todo-- code list)                                                                                                                                                                                                                                            |
| `results[].object.model_gear_system`          | `string`   | `false`  |           | Model gear system e.g. `Modelname`                                                                                                                                                                                                                                                           |
| `results[].object.gear_count`                 | `integer`  | `false`  |           | Gear count e.g. `24`                                                                                                                                                                                                                                                                         |
| `results[].object.gears`                      | `string`   | `false`  |           | Gear description e.g. `Shimano Alivio`                                                                                                                                                                                                                                                       |
| `results[].object.description_short`          | `string`   | `false`  |           | Description e.g. `Batavus Crescendo`                                                                                                                                                                                                                                                         |
| `results[].object.description`                | `string`   | `false`  |           | Description long e.g. `Some text`                                                                                                                                                                                                                                                            |
| `results[].object.purchase_price_cents`       | `integer`  | `false`  |           | Purchase price in cents e.g. `80000`                                                                                                                                                                                                                                                         |
| `results[].object.sales_price_cents`          | `integer`  | `false`  |           | Sales price in cents e.g. `129900`                                                                                                                                                                                                                                                           |
| `results[].object.rrp_cents`                  | `integer`  | `false`  |           | Recommended retail price in cents e.g. `129900`                                                                                                                                                                                                                                              |
| `results[].object.ecommerce`                  | `boolean`  | `false`  |           | `true` if available for e-commerce e.g. `false`                                                                                                                                                                                                                                              |
| `results[].object.ecommerce_price_cents`      | `integer`  | `false`  |           | E-commerce sales price e.g. `129900`                                                                                                                                                                                                                                                         |
| `results[].object.nett_weight_kg`             | `double`   | `false`  |           | Weight (kg) e.g. `11.2`                                                                                                                                                                                                                                                                      |
| `results[].object.gross_weight_kg`            | `double`   | `false`  |           | Weight gross (kg) e.g. `12`                                                                                                                                                                                                                                                                  |
| `results[].object.supplier_invoice_reference` | `string`   | `false`  |           | Supplier invoice reference e.g. `INV-1121221`                                                                                                                                                                                                                                                |
| `results[].object.supplier_order_reference`   | `string`   | `false`  |           | Supplier order reference e.g. `ORDER-1121221`                                                                                                                                                                                                                                                |
| `results[].object.custom_variable_1`          | `string`   | `false`  |           | Custom variable 1 e.g. `Some value`                                                                                                                                                                                                                                                          |
| `results[].object.custom_variable_2`          | `string`   | `false`  |           | Custom variable 2 e.g. `Some value`                                                                                                                                                                                                                                                          |
| `results[].object.custom_variable_3`          | `string`   | `false`  |           | Custom variable 3 e.g. `Some value`                                                                                                                                                                                                                                                          |
| `results[].object.custom_variable_4`          | `string`   | `false`  |           | Custom variable 4 e.g. `Some value`                                                                                                                                                                                                                                                          |
| `results[].object.warranty_type`              | `integer`  | `false`  |           | Warranty type e.g. `2`                                                                                                                                                                                                                                                                       |
| `results[].skipped_fields`                    | `string[]` | `false`  | `Yes`     | Array of fields which are ignored in the update. Omitted if not present                                                                                                                                                                                                                      |
| `results[].warnings`                          | `object[]` | `false`  | `Yes`     | Array of warnings, omitted if status `error` or `success`                                                                                                                                                                                                                                    |
| `results[].warnings[].field`                  | `?string`  | `false`  |           | The field which the warning is related to if applicable e.g. `ecommerce_price_cents`                                                                                                                                                                                                         |
| `results[].warnings[].message`                | `string`   | `false`  |           | The warning message                                                                                                                                                                                                                                                                          |
| `results[].error`                             | `object`   | `false`  | `Yes`     | Object with error info. Only present when status `error`                                                                                                                                                                                                                                     |
| `results[].error.message`                     | `string`   | `false`  |           | The error message e.g. `Maximaal 150 updates toegestaan per aanvraag`                                                                                                                                                                                                                        |

> HTTP request

```http
PATCH /api/beta/stock-objects/batch/update.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json

{
    "updates": [
        {
            "filter": {
                "stock_object_ids": [
                    26058,
                    26042
                ]
            },
            "article_main_group": 1,
            "article_group": "B",
            "article_sub_group": 1,
            "model_name": "New model name",
            "model_year": 2025,
            "primary_color": "ZWART",
            "secondary_color": "ZWART",
            "custom_variable_2": "Some new value",
            "frame_material": "carbon",
            "customer_group": "Heren",
            "warranty_type": 2
        },
        {
            "filter": {
                "barcode": "8719461035866"
            },
            "article_main_group": 2,
            "article_group": "B",
            "model_name": "New model name 8719461035866",
            "primary_color": "ZWART",
            "secondary_color": "ZWART",
            "custom_variable_2": "68de5167c84b3",
            "ecommerce_price_cents": "test",
            "frame_material": "INVALID-MATERIAL",
            "unknown_field": "bar",
            "warranty_type": 2
        },
        {
            "filter": {
                "barcode": "unknown-barcode"
            },
            "article_main_group": 2,
            "article_group": "B",
            "model_name": "New model name",
            "primary_color": "ZWART",
            "secondary_color": "ZWART",
            "custom_variable_2": "68de5167c84b6",
            "ecommerce_price_cents": "test",
            "frame_material": "FOO",
            "unknown_field": "bar",
            "warranty_type": 2
        }
    ]
}
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 19744

{
    "results": [
        {
            "stock_object_id": 26042,
            "result": "success",
            "object": {
                "stock_object_id": 26042,
                "is_reserved": false,
                "is_demo": false,
                "object_reference": "",
                "barcode": "3323",
                "article_id": "0298",
                "brand_name": "Batavus",
                "brand_id": 1759,
                "model_name": "New model name",
                "article_main_group": 1,
                "article_group": "B",
                "article_sub_group": 1,
                "frame_type": "WOMEN",
                "model_year": 2025,
                "frame_height": 53,
                "frame_size_supplier": "",
                "wheel_size": 28,
                "customer_group": "MEN",
                "frame_material": "CARBON",
                "color": "Scumzilver",
                "primary_color": "BLACK",
                "secondary_color": "BLACK",
                "type_brake_system_front": "",
                "brand_brake_system_front": "",
                "model_brake_system_front": "",
                "type_brake_system_rear": "",
                "brand_brake_system_rear": "",
                "model_brake_system_rear": "",
                "type_gear_system": "",
                "brand_gear_system": "",
                "model_gear_system": "",
                "gear_count": 24,
                "gears": "Shimano Alivio",
                "description_short": "",
                "description": "",
                "purchase_price_cents": 0,
                "sales_price_cents": 0,
                "rrp_cents": 0,
                "ecommerce": false,
                "ecommerce_price_cents": 0,
                "nett_weight_kg": 0,
                "gross_weight_kg": 0,
                "supplier_invoice_reference": "",
                "supplier_order_reference": "",
                "custom_variable_1": "",
                "custom_variable_2": "Some new value",
                "custom_variable_3": "",
                "custom_variable_4": "",
                "warranty_type": 2
            },
            "skipped_fields": [],
            "warnings": []
        },
        {
            "stock_object_id": 26058,
            "result": "error",
            "error": {
                "message": "Object with number 26058 is not found"
            },
            "skipped_fields": [],
            "warnings": []
        },
        {
            "barcode": "8719461035866",
            "result": "partial",
            "object": {
                "stock_object_id": 24304,
                "is_reserved": false,
                "is_demo": false,
                "object_reference": "",
                "barcode": "8719461035866",
                "article_id": "CT7NDH56JEBMT",
                "brand_name": "Cortina",
                "brand_id": 1941,
                "model_name": "New model name 8719461035866",
                "article_main_group": 1,
                "article_group": "B",
                "article_sub_group": 1,
                "frame_type": "MEN",
                "model_year": 2021,
                "frame_height": 56,
                "frame_size_supplier": "",
                "wheel_size": 28,
                "customer_group": "MEN",
                "frame_material": "ALUMINIUM",
                "color": "Jet Black Matt",
                "primary_color": "BLACK",
                "secondary_color": "BLACK",
                "type_brake_system_front": "RK",
                "brand_brake_system_front": "SHIMANO",
                "model_brake_system_front": "",
                "type_brake_system_rear": "RK",
                "brand_brake_system_rear": "SHIMANO",
                "model_brake_system_rear": "",
                "type_gear_system": "",
                "brand_gear_system": "SHIMANO",
                "model_gear_system": "NAAF",
                "gear_count": 7,
                "gears": "",
                "description_short": "Cortina U4 H56 Jet Black Matt ND7",
                "description": "Cortina Transport U4 herenfiets in framemaat 56cm. Kleur: Jet Black Matt. Uitgerust met achter een Shimano Nexus 7-traps versnellingsnaaf met rollerbrake en voor een Shimano naafdynamo met rollerbrake. Opvallende details: aluminium frame, stuurslot, voordrager. Kleurnummer: UZZ 69005 Matt.",
                "purchase_price_cents": 44902,
                "sales_price_cents": 79900,
                "rrp_cents": 79900,
                "ecommerce": true,
                "ecommerce_price_cents": 0,
                "nett_weight_kg": 0,
                "gross_weight_kg": 23.8,
                "supplier_invoice_reference": "",
                "supplier_order_reference": "F.24304",
                "custom_variable_1": "",
                "custom_variable_2": "68de518217573",
                "custom_variable_3": "",
                "custom_variable_4": "",
                "warranty_type": 2
            },
            "skipped_fields": [
                "article_main_group",
                "article_group",
                "ecommerce_price_cents",
                "frame_material",
                "unknown_field"
            ],
            "warnings": [
                {
                    "field": "article_main_group",
                    "message": "article_main_group, article_group, article_sub_group are required when updating article_main_group"
                },
                {
                    "field": "article_group",
                    "message": "article_main_group, article_group, article_sub_group are required when updating article_main_group"
                },
                {
                    "field": "frame_material",
                    "message": "INVALID-MATERIAL is not a valid option"
                },
                {
                    "field": "ecommerce_price_cents",
                    "message": "\"test\" is not a valid numeric value"
                }
            ]
        },
        {
            "barcode": "8719461035866",
            "result": "partial",
            "object": {
                "stock_object_id": 24222,
                "is_reserved": false,
                "is_demo": false,
                "object_reference": "",
                "barcode": "8719461035866",
                "article_id": "CT7NDH56JEBMT",
                "brand_name": "Cortina",
                "brand_id": 1941,
                "model_name": "New model name 8719461035866",
                "article_main_group": 1,
                "article_group": "B",
                "article_sub_group": 1,
                "frame_type": "MEN",
                "model_year": 2021,
                "frame_height": 56,
                "frame_size_supplier": "56",
                "wheel_size": 28,
                "customer_group": "MEN",
                "frame_material": "56",
                "color": "Jet Black Matt",
                "primary_color": "BLACK",
                "secondary_color": "BLACK",
                "type_brake_system_front": "RK",
                "brand_brake_system_front": "SHIMANO",
                "model_brake_system_front": "",
                "type_brake_system_rear": "RK",
                "brand_brake_system_rear": "SHIMANO",
                "model_brake_system_rear": "",
                "type_gear_system": "SHIMANO",
                "brand_gear_system": "SHIMANO",
                "model_gear_system": "NAAF",
                "gear_count": 7,
                "gears": "",
                "description_short": "Cortina U4 H56 Jet Black Matt ND7",
                "description": "Cortina Transport U4 herenfiets in framemaat 56cm. Kleur: Jet Black Matt. Uitgerust met achter een Shimano Nexus 7-traps versnellingsnaaf met rollerbrake en voor een Shimano naafdynamo met rollerbrake. Opvallende details: aluminium frame, stuurslot, voordrager. Kleurnummer: UZZ 69005 Matt.",
                "purchase_price_cents": 52823,
                "sales_price_cents": 79900,
                "rrp_cents": 79900,
                "ecommerce": true,
                "ecommerce_price_cents": 0,
                "nett_weight_kg": 0,
                "gross_weight_kg": 23.8,
                "supplier_invoice_reference": "",
                "supplier_order_reference": "",
                "custom_variable_1": "",
                "custom_variable_2": "68de518217573",
                "custom_variable_3": "",
                "custom_variable_4": "",
                "warranty_type": 2
            },
            "skipped_fields": [
                "article_main_group",
                "article_group",
                "ecommerce_price_cents",
                "frame_material",
                "unknown_field"
            ],
            "warnings": [
                {
                    "field": "article_main_group",
                    "message": "article_main_group, article_group, article_sub_group are required when updating article_main_group"
                },
                {
                    "field": "article_group",
                    "message": "article_main_group, article_group, article_sub_group are required when updating article_main_group"
                },
                {
                    "field": "frame_material",
                    "message": "INVALID-MATERIAL is not a valid option"
                },
                {
                    "field": "ecommerce_price_cents",
                    "message": "\"test\" is not a valid numeric value"
                }
            ]
        },
        {
            "barcode": "unknown-barcode",
            "result": "error",
            "error": {
                "message": "No new & unsold objects found with barcode \"unknown-barcode\""
            },
            "skipped_fields": [],
            "warnings": []
        }
    ]
}
```


## Stock object (beta) ##

Get info for a specific stock object

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/beta/stock-objects/:stock_object_id.json</h6>
	</div>
</div>

| **URI parameter** | **Type**  | **Description**                  |
|-------------------|-----------|----------------------------------|
| `stock_object_id` | `integer` | The stock object ID e.g. `12122` |


> HTTP request

```http
GET /api/beta/stock-objects/1333.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json

```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 19744

{
.....
}
```


