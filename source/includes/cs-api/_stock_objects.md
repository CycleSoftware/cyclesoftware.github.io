# Stock objects #


## Stock object info ##

Get info for a specific stock object

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/stock-objects/:stock_object_id.json</h6>
	</div>
</div>

| **URI parameter** | **Type**  | **Description**                  |
|-------------------|-----------|----------------------------------|
| `stock_object_id` | `integer` | The stock object ID e.g. `12122` |

### Result properties

| Property          | Type      | Omittable | Description |
|-------------------|-----------|-----------|-------------|
| `stock_object_id` | `integer` |           | ....        |

| Property                              | Type       | Nullable   | Description                                                                               |
|---------------------------------------|------------|------------|-------------------------------------------------------------------------------------------|
| `customer_id`                         | `?integer` | `true`     | If sold, the customer ID of the rider                                                     |
| `stock_object_id`                     | `integer`  | `false`    | The unique stock object ID within the account e.g. `99999`                                |
| `store_id`                            | `integer`  | `false`    | Store ID e.g. `1`                                                                         |
| `sales_order_id`                      | `?integer` | `true`     | If sold with a sales order, the sales order ID. `null` if not set.                        |
| `sales_transaction_number`            | `?integer` | `true`     | If sold and invoiced, the invoice number. `null` if not set.                              |
| `status`                              | `object`   | `false`    | Object with stock-status data                                                             |
| `status.available`                    | `boolean`  | `false`    | `true` if the object is not-sold and in stock e.g. `true`                                 |
| `status.expected_at`                  | `?date`    | `true`     | The expected delivery date if not `available`. `null` if unknown                          |
| `status.is_demo`                      | `boolean`  | `false`    | `true` if the object is marked as demo e.g. `false`                                       |
| `status.is_rental`                    | `boolean`  | `false`    | `true` if the object is a rental object e.g. `false`                                      |
| `status.is_reserved`                  | `boolean`  | `false`    | `true` if the object is reserved e.g. `false`                                             |
| `status.is_sold`                      | `boolean`  | `false`    | `true` if the object is sold e.g. `false`                                                 |
| `status.is_used`                      | `boolean`  | `false`    | `true` if the object is used e.g. `false`                                                 |
| `status.km_age`                       | `integer`  | `false`    | Kilometer age e.g. `0`                                                                    |
| `identification`                      | `object`   | `false`    | Object with identification. If the value is not available the property is not present/    |
| `identification.frame_number`         | `string`   | `omitable` | The frame number e.g. `FR0000010`                                                         |
| `identification.key_number`           | `string`   | `omitable` | The key number e.g. `SL10000`                                                             |
| `identification.key_number_2`         | `string`   | `omitable` | The key number 2 e.g. `SL100001`                                                          |
| `identification.lock_number`          | `string`   | `omitable` | The lock number e.g. `L11122`                                                             |
| `identification.lock_number_2`        | `string`   | `omitable` | The lock number 2 e.g. `L11122-2`                                                         |
| `identification.battery_number`       | `string`   | `omitable` | The battery number e.g. `BAT11221`                                                        |
| `identification.battery_number_2`     | `string`   | `omitable` | The battery number 2 e.g. `BAT11222`                                                      |
| `identification.engine_number`        | `string`   | `omitable` | The engine number e.g. `EN-11111`                                                         |
| `identification.serial_number`        | `string`   | `omitable` | The serial number e.g. `SL3332323`                                                        |
| `identification.imei_number`          | `string`   | `omitable` | The imei number e.g. `IMEI23322323`                                                       |
| `identification.license_plate_number` | `string`   | `omitable` | The license plate number e.g. `xx-yy-zz`                                                  |
| `identification.velopass_code`        | `string`   | `omitable` | The velopass code e.g. `VP12EH6745`                                                       |
| `images`                              | `object[]` | `false`    | List of images                                                                            |
| `images[].date_modified`              | `datetime` | `false`    | Date modification e.g. `2025-10-01 12:00:00`                                              |
| `images[].url_large`                  | `string`   | `false`    | URL the large image e.g. `https://cdn.cyclesoftware.nl/app/img/artPic_public_L_1.jpg`     |
| `images[].url_thumb`                  | `string`   | `false`    | URL the thumbnail image e.g. `https://cdn.cyclesoftware.nl/app/img/artPic_public_T_1.jpg` |
| `object`                              | `object`   | `false`    | Same structure as object in `results[].object` of the batch update endpoint result        |

> HTTP request

```http
GET /api/v1/stock-objects/1333.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json

```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 2898

{
    "stock_object_id": 26034,
    "store_id": 1,
    "customer_id": null,
    "sales_order_id": null,
    "sales_transaction_number": null,
    "status": {
        "available": true,
        "expected_at": null,
        "is_demo": false,
        "is_used": false,
        "is_rental": false,
        "is_sold": false,
        "is_reserved": false,
        "km_age": 1000
    },
    "object": {
        "stock_object_id": 26034,
        "store_id": 1,
        "is_reserved": false,
        "is_demo": false,
        "object_reference": "REF1",
        "barcode": "8713568461597",
        "article_id": "BE102029",
        "brand_name": "BATAVUS",
        "brand_id": 1759,
        "model_name": "Finez E-Go-D Power Sport",
        "article_main_group": 1,
        "article_group": "A",
        "article_sub_group": 1,
        "frame_type": "LAGE INSTAP",
        "model_year": 2024,
        "frame_height": 53,
        "frame_size_supplier": "",
        "wheel_size": 28,
        "customer_group": "DAMES",
        "frame_material": "ALUMINIUM",
        "color": "Zwart Glans",
        "primary_color": "ZWART",
        "secondary_color": "",
        "type_brake_system_front": "SH",
        "brand_brake_system_front": "MAGURA",
        "model_brake_system_front": "HYDRAULISCHE SCHIJFREM",
        "type_brake_system_rear": "SH",
        "brand_brake_system_rear": "MAGURA",
        "model_brake_system_rear": "HYDRAULISCHE SCHIJFREM",
        "type_gear_system": "DERAILLEUR",
        "brand_gear_system": "SHIMANO",
        "model_gear_system": "CUES",
        "gear_count": 10,
        "description_short": "FINEZ E-GO PT SPORT BES-3 DV10 NERO 53 NO BATT",
        "description": "FINEZ E-GO PT SPORT BES-3 DV10 NERO 53 NO BATT",
        "purchase_price_cents": 273896,
        "sales_price_cents": 369900,
        "rrp_cents": 389900,
        "ecommerce": true,
        "ecommerce_price_cents": 389900,
        "nett_weight_kg": 31,
        "gross_weight_kg": 0,
        "supplier_invoice_reference": "",
        "supplier_order_reference": "",
        "custom_variable_1": "",
        "custom_variable_2": "",
        "custom_variable_3": "",
        "custom_variable_4": "",
        "warranty_type": 0
    },
    "identification": {
        "frame_number": "FR1",
        "key_number": "SL1",
        "key_number_2": "SL2",
        "lock_number": "L1",
        "lock_number_2": "L2",
        "battery_number": "AC1",
        "battery_number_2": "AC2",
        "engine_number": "EN1",
        "serial_number": "SR1",
        "imei_number": "IMEI",
        "license_plate_number": "11-22-33"
    },
    "images": [
        {
            "date_modified": "2024-12-04 13:54:31",
            "url_thumb": "https://cdn.cyclesoftware.nl/app/img/artPic_public_T_2254286.jpg",
            "url_large": "https://cdn.cyclesoftware.nl/app/img/artPic_public_L_2254286.jpg"
        }
    ]
}
```


## Stock object batch updates ##

Apply batch updates to stock objects. You can only update stock objects which are not sold and are not used.

***Authentication mechanism***

- Basic HTTP Authentication
- Scopes: `resources`

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">PATCH</i>
		<h6>/api/v1/stock-objects/batch/update.json</h6>
	</div>
</div>

### Request properties

| Property  | Type       | Required | Description                                   |
|-----------|------------|----------|-----------------------------------------------|
| `updates` | `object[]` | `true`   | Array with data objects, maximum of 150 items |

### Request properties

All properties except `filter` may be omitted in the request. If you update `article_main_group`, `article_group`,
`article_sub_group` all properties should be present.

| Property                               | Type        | Nullable   | Omittable                                                                                                                               | Description     |
|----------------------------------------|-------------|------------|-----------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| `updates`                              | `object[]`  | `false`    | List of updates                                                                                                                         | List of updates |
| `updates[].filter`                     | `object`    | `false`    | Filter that contains information about which objects to update                                                                          |
| `updates[].filter.barcode`             | `string`    | `omitable` | Barcode of stock object to update                                                                                                       |
| `updates[].filter.stock_object_ids`    | `integer[]` | `omitable` | List of stock object ids to update                                                                                                      |
| `updates[].is_reserved`                | `boolean`   |            | `true` if object is reserved e.g. `false`                                                                                               |
| `updates[].is_demo`                    | `boolean`   |            | `true` if object is demo e.g. `false`                                                                                                   |
| `updates[].object_reference`           | `string`    |            | Object reference e.g. `F23322332`                                                                                                       |
| `updates[].barcode`                    | `string`    |            | Barcode of object e.g. `878734843384`                                                                                                   |
| `updates[].article_id`                 | `string`    |            | Article ID of object e.g. `0298`                                                                                                        |
| `updates[].brand_id`                   | `integer`   |            | Brand ID of object e.g. `1759` (codelist: `/api/v1/common/bike-brands.json`)                                                            |
| `updates[].model_name`                 | `string`    |            | Model name of object e.g. `New model name`                                                                                              |
| `updates[].article_main_group`         | `integer`   |            | Main article group ID e.g. `1` - should always be `1` for bikes (see code list `/api/v4/articledata/codelist/tree/bikes.json`)          |
| `updates[].article_group`              | `string`    |            | Article group ID e.g. `A` (see code list `/api/v4/articledata/codelist/tree/bikes.json`)                                                |
| `updates[].article_sub_group`          | `integer`   |            | Sub article group ID e.g. `1` (see code list `/api/v4/articledata/codelist/tree/bikes.json`)                                            |
| `updates[].frame_type`                 | `string`    |            | Frame type of object e.g. `WOMEN` (if language is nl_NL this field will be in Dutch, see `/api/v4/articledata/codelist/frame.json`)     |
| `updates[].model_year`                 | `integer`   |            | Model year of object  e.g. `2025`                                                                                                       |
| `updates[].frame_height`               | `integer`   |            | Frame height in CM e.g. `53`                                                                                                            |
| `updates[].frame_size_supplier`        | `string`    |            | Frame size description e.g. `M`                                                                                                         |
| `updates[].wheel_size`                 | `integer`   |            | Wheel size in inch e.g. `28`                                                                                                            |
| `updates[].customer_group`             | `string`    |            | Customer group e.g. `MEN`  (if language is nl_NL this field will be in Dutch, see `/api/v4/articledata/codelist/customer_group.json`)   |
| `updates[].frame_material`             | `string`    |            | Frame material e.g. `CARBON` (if language is nl_NL this field will be in Dutch, see `/api/v4/articledata/codelist/frame_material.json`) |
| `updates[].color`                      | `string`    |            | Color description e.g. `Scumzilver`                                                                                                     |
| `updates[].primary_color`              | `string`    |            | Primary color e.g. `BLACK` (if language is nl_NL this field will be in Dutch, see `/api/v4/articledata/codelist/base_color.json`)       |
| `updates[].secondary_color`            | `string`    |            | Secondary color e.g. `BLACK` (if language is nl_NL this field will be in Dutch, see `/api/v4/articledata/codelist/base_color.json`)     |
| `updates[].type_brake_system_front`    | `string`    |            | Type brake system front e.g. `BK` (see `/api/v4/articledata/codelist/brake_system.json`)                                                |
| `updates[].brand_brake_system_front`   | `string`    |            | Brand brake system front e.g. `SRAM` (see `/api/v4/articledata/codelist/brand.json`)                                                    |
| `updates[].model_brake_system_front`   | `string`    |            | Model brake system front e.g. `Modelname`                                                                                               |
| `updates[].type_brake_system_rear`     | `string`    |            | Type brake system rear e.g. ``   (see `/api/v4/articledata/codelist/brake_system.json`)                                                 |
| `updates[].brand_brake_system_rear`    | `string`    |            | Brand brake system rear e.g. `SRAM` (see `/api/v4/articledata/codelist/brand.json`)                                                     |
| `updates[].model_brake_system_rear`    | `string`    |            | Model brake system rear e.g. `Modelname`                                                                                                |
| `updates[].type_gear_system`           | `string`    |            | Type gear system e.g. `DERAILLEUR` (see `/api/v4/articledata/codelist/gear_system.json`)                                                |
| `updates[].brand_gear_system`          | `string`    |            | Brand gear system e.g. `SRAM` (see `/api/v4/articledata/codelist/brand.json`)                                                           |
| `updates[].model_gear_system`          | `string`    |            | Model gear system e.g. `Modelname`                                                                                                      |
| `updates[].gear_count`                 | `integer`   |            | Gear count e.g. `24`                                                                                                                    |
| `updates[].description_short`          | `string`    |            | Description e.g. `Batavus Crescendo`                                                                                                    |
| `updates[].description`                | `string`    |            | Description long e.g. `Some text`                                                                                                       |
| `updates[].purchase_price_cents`       | `integer`   |            | Purchase price in cents e.g. `80000`                                                                                                    |
| `updates[].sales_price_cents`          | `integer`   |            | Sales price in cents e.g. `129900`                                                                                                      |
| `updates[].rrp_cents`                  | `integer`   |            | Recommended retail price in cents e.g. `129900`                                                                                         |
| `updates[].ecommerce`                  | `boolean`   |            | `true` if available for e-commerce e.g. `false`                                                                                         |
| `updates[].ecommerce_price_cents`      | `integer`   |            | E-commerce sales price e.g. `129900`                                                                                                    |
| `updates[].nett_weight_kg`             | `double`    |            | Weight (kg) e.g. `11.2`                                                                                                                 |
| `updates[].gross_weight_kg`            | `double`    |            | Weight gross (kg) e.g. `12`                                                                                                             |
| `updates[].supplier_invoice_reference` | `string`    |            | Supplier invoice reference e.g. `INV-1121221`                                                                                           |
| `updates[].supplier_order_reference`   | `string`    |            | Supplier order reference e.g. `ORDER-1121221`                                                                                           |
| `updates[].custom_variable_1`          | `string`    |            | Custom variable 1 e.g. `Some value`                                                                                                     |
| `updates[].custom_variable_2`          | `string`    |            | Custom variable 2 e.g. `Some value`                                                                                                     |
| `updates[].custom_variable_3`          | `string`    |            | Custom variable 3 e.g. `Some value`                                                                                                     |
| `updates[].custom_variable_4`          | `string`    |            | Custom variable 4 e.g. `Some value`                                                                                                     |
| `updates[].warranty_duration_months`   | `integer`   | `omitable` | Warranty duration in months if set.                                                                                                     |
| `updates[].warranty_type`              | `integer`   |            | Warranty type e.g. `2` (see `/api/v1/common/enum/warranty-types.json`)                                                                  |

### Result properties

| Property                                      | Type       | Omittable | Description                                                                                                                                                                                                                                                                                 |
|-----------------------------------------------|------------|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `results`                                     | `object[]` |           | List of result objects                                                                                                                                                                                                                                                                      |
| `results[].result`                            | `string`   |           | `success` (all fields updated),  <br/>`partial` (not all fields could be updated see `results[].skipped_fields` <br/>`success_with_warnings` (all fields updated with some warnings, see `results[].warnings`) <br/>`error` (article not updated or created, see `results[].error.message`) |
| `results[].object`                            | `object`   | `Yes`     | Object with resulting stock object details, omitted when an error occurs                                                                                                                                                                                                                    |
| `results[].stock_object_id`                   | `integer`  | `Yes`     | If present the update is based on filter.stock_object_ids and this field is the stock-object affected e.g. `26042`                                                                                                                                                                          |
| `results[].barcode`                           | `integer`  | `Yes`     | If present the update is based on filter.barcode e.g. `26042`                                                                                                                                                                                                                               |
| `results[].object.stock_object_id`            | `integer`  |           | Stock object ID e.g. `26042`                                                                                                                                                                                                                                                                |
| `results[].object.store_id`                   | `boolean`  |           | The store ID of the object, e.g. `1` (readonly)                                                                                                                                                                                                                                             |
| `results[].object.is_reserved`                | `boolean`  |           | `true` if object is reserved e.g. `false`                                                                                                                                                                                                                                                   |
| `results[].object.is_demo`                    | `boolean`  |           | `true` if object is demo e.g. `false`                                                                                                                                                                                                                                                       |
| `results[].object.object_reference`           | `string`   |           | Object reference e.g. `F23322332`                                                                                                                                                                                                                                                           |
| `results[].object.barcode`                    | `string`   |           | Barcode of object e.g. `878734843384`                                                                                                                                                                                                                                                       |
| `results[].object.article_id`                 | `string`   |           | Article ID of object e.g. `0298`                                                                                                                                                                                                                                                            |
| `results[].object.brand_name`                 | `string`   |           | Brand name of object e.g. `Batavus` (readonly)                                                                                                                                                                                                                                              |
| `results[].object.brand_id`                   | `integer`  |           | Brand ID of object e.g. `1759` (codelist: `/api/v1/common/bike-brands.json`)                                                                                                                                                                                                                |
| `results[].object.model_name`                 | `string`   |           | Model name of object e.g. `New model name`                                                                                                                                                                                                                                                  |
| `results[].object.article_main_group`         | `integer`  |           | Main article group ID e.g. `1` - should always be `1` for bikes (see code list `/api/v4/articledata/codelist/tree/bikes.json`)                                                                                                                                                              |
| `results[].object.article_group`              | `string`   |           | Article group ID e.g. `A` (see code list `/api/v4/articledata/codelist/tree/bikes.json`)                                                                                                                                                                                                    |
| `results[].object.article_sub_group`          | `integer`  |           | Sub article group ID e.g. `1` (see code list `/api/v4/articledata/codelist/tree/bikes.json`)                                                                                                                                                                                                |
| `results[].object.frame_type`                 | `string`   |           | Frame type of object e.g. `WOMEN` (if language is nl_NL this field will be in Dutch, see `/api/v4/articledata/codelist/frame.json`)                                                                                                                                                         |
| `results[].object.model_year`                 | `integer`  |           | Model year of object  e.g. `2025`                                                                                                                                                                                                                                                           |
| `results[].object.frame_height`               | `integer`  |           | Frame height in CM e.g. `53`                                                                                                                                                                                                                                                                |
| `results[].object.frame_size_supplier`        | `string`   |           | Frame size description e.g. `M`                                                                                                                                                                                                                                                             |
| `results[].object.wheel_size`                 | `integer`  |           | Wheel size in inch e.g. `28`                                                                                                                                                                                                                                                                |
| `results[].object.customer_group`             | `string`   |           | Customer group e.g. `MEN`  (if language is nl_NL this field will be in Dutch, see `/api/v4/articledata/codelist/customer_group.json`)                                                                                                                                                       |
| `results[].object.frame_material`             | `string`   |           | Frame material e.g. `CARBON` (if language is nl_NL this field will be in Dutch, see `/api/v4/articledata/codelist/frame_material.json`)                                                                                                                                                     |
| `results[].object.color`                      | `string`   |           | Color description e.g. `Scumzilver`                                                                                                                                                                                                                                                         |
| `results[].object.primary_color`              | `string`   |           | Primary color e.g. `BLACK` (if language is nl_NL this field will be in Dutch, see `/api/v4/articledata/codelist/base_color.json`)                                                                                                                                                           |
| `results[].object.secondary_color`            | `string`   |           | Secondary color e.g. `BLACK` (if language is nl_NL this field will be in Dutch, see `/api/v4/articledata/codelist/base_color.json`)                                                                                                                                                         |
| `results[].object.type_brake_system_front`    | `string`   |           | Type brake system front e.g. `BK` (see `/api/v4/articledata/codelist/brake_system.json`)                                                                                                                                                                                                    |
| `results[].object.brand_brake_system_front`   | `string`   |           | Brand brake system front e.g. `SRAM` (see `/api/v4/articledata/codelist/brand.json`)                                                                                                                                                                                                        |
| `results[].object.model_brake_system_front`   | `string`   |           | Model brake system front e.g. `Modelname`                                                                                                                                                                                                                                                   |
| `results[].object.type_brake_system_rear`     | `string`   |           | Type brake system rear e.g. ``   (see `/api/v4/articledata/codelist/brake_system.json`)                                                                                                                                                                                                     |
| `results[].object.brand_brake_system_rear`    | `string`   |           | Brand brake system rear e.g. `SRAM` (see `/api/v4/articledata/codelist/brand.json`)                                                                                                                                                                                                         |
| `results[].object.model_brake_system_rear`    | `string`   |           | Model brake system rear e.g. `Modelname`                                                                                                                                                                                                                                                    |
| `results[].object.type_gear_system`           | `string`   |           | Type gear system e.g. `DERAILLEUR` (see `/api/v4/articledata/codelist/gear_system.json`)                                                                                                                                                                                                    |
| `results[].object.brand_gear_system`          | `string`   |           | Brand gear system e.g. `SRAM` (see `/api/v4/articledata/codelist/brand.json`)                                                                                                                                                                                                               |
| `results[].object.model_gear_system`          | `string`   |           | Model gear system e.g. `Modelname`                                                                                                                                                                                                                                                          |
| `results[].object.gear_count`                 | `integer`  |           | Gear count e.g. `24`                                                                                                                                                                                                                                                                        |
| `results[].object.description_short`          | `string`   |           | Description e.g. `Batavus Crescendo`                                                                                                                                                                                                                                                        |
| `results[].object.description`                | `string`   |           | Description long e.g. `Some text`                                                                                                                                                                                                                                                           |
| `results[].object.purchase_price_cents`       | `integer`  |           | Purchase price in cents e.g. `80000`                                                                                                                                                                                                                                                        |
| `results[].object.sales_price_cents`          | `integer`  |           | Sales price in cents e.g. `129900`                                                                                                                                                                                                                                                          |
| `results[].object.rrp_cents`                  | `integer`  |           | Recommended retail price in cents e.g. `129900`                                                                                                                                                                                                                                             |
| `results[].object.ecommerce`                  | `boolean`  |           | `true` if available for e-commerce e.g. `false`                                                                                                                                                                                                                                             |
| `results[].object.ecommerce_price_cents`      | `integer`  |           | E-commerce sales price e.g. `129900`                                                                                                                                                                                                                                                        |
| `results[].object.nett_weight_kg`             | `double`   |           | Weight (kg) e.g. `11.2`                                                                                                                                                                                                                                                                     |
| `results[].object.gross_weight_kg`            | `double`   |           | Weight gross (kg) e.g. `12`                                                                                                                                                                                                                                                                 |
| `results[].object.supplier_invoice_reference` | `string`   |           | Supplier invoice reference e.g. `INV-1121221`                                                                                                                                                                                                                                               |
| `results[].object.supplier_order_reference`   | `string`   |           | Supplier order reference e.g. `ORDER-1121221`                                                                                                                                                                                                                                               |
| `results[].object.custom_variable_1`          | `string`   |           | Custom variable 1 e.g. `Some value`                                                                                                                                                                                                                                                         |
| `results[].object.custom_variable_2`          | `string`   |           | Custom variable 2 e.g. `Some value`                                                                                                                                                                                                                                                         |
| `results[].object.custom_variable_3`          | `string`   |           | Custom variable 3 e.g. `Some value`                                                                                                                                                                                                                                                         |
| `results[].object.custom_variable_4`          | `string`   |           | Custom variable 4 e.g. `Some value`                                                                                                                                                                                                                                                         |
| `results[].object.warranty_duration_months`   | `integer`  | `Yes`     | Warranty duration in months if set.                                                                                                                                                                                                                                                         |
| `results[].object.warranty_type`              | `integer`  |           | Warranty type e.g. `2` (see `/api/v1/common/enum/warranty-types.json`)                                                                                                                                                                                                                      |
| `results[].skipped_fields`                    | `string[]` | `Yes`     | List of fields which are ignored in the update. Omitted if not present                                                                                                                                                                                                                      |
| `results[].warnings`                          | `object[]` | `Yes`     | List of warnings, omitted if status `error` or `success`                                                                                                                                                                                                                                    |
| `results[].warnings[].field`                  | `?string`  |           | The field which the warning is related to if applicable e.g. `ecommerce_price_cents`                                                                                                                                                                                                        |
| `results[].warnings[].message`                | `string`   |           | The warning message                                                                                                                                                                                                                                                                         |
| `results[].warnings[].code_list`              | `string`   | `Yes`     | The URL the the codelist if this applies to the `field` e.g. `https://s01.cyclesoftware.nl/api/v4/articledata/codelist/tree/bikes.json`                                                                                                                                                     |
| `results[].error`                             | `object`   | `Yes`     | Object with error info. Only present when status `error`                                                                                                                                                                                                                                    |
| `results[].error.message`                     | `string`   |           | The error message in your locale e.g. `Maximaal 150 updates toegestaan per aanvraag`                                                                                                                                                                                                        |

> HTTP request

```http
PATCH /api/v1/stock-objects/batch/update.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json

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
                "model_gear_system": "HUB",
                "gear_count": 7,
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
                    "message": "article_main_group, article_group, article_sub_group are required when updating article_main_group",
                    "code_list": "https://api.cyclesoftware.nl/api/v4/articledata/codelist/tree/bikes.json"
                },
                {
                    "field": "article_group",
                    "message": "article_main_group, article_group, article_sub_group are required when updating article_main_group",
                    "code_list": "https://api.cyclesoftware.nl/api/v4/articledata/codelist/tree/bikes.json"
                },
                {
                    "field": "frame_material",
                    "message": "INVALID-MATERIAL is not a valid option",
                    "code_list": "https://api.cyclesoftware.nl/api/v4/articledata/codelist/frame_material.json"
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
                "model_gear_system": "HUB",
                "gear_count": 7,
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
                    "message": "article_main_group, article_group, article_sub_group are required when updating article_main_group",
                    "code_list": "https://api.cyclesoftware.nl/api/v4/articledata/codelist/tree/bikes.json"
                },
                {
                    "field": "article_group",
                    "message": "article_main_group, article_group, article_sub_group are required when updating article_main_group",
                    "code_list": "https://api.cyclesoftware.nl/api/v4/articledata/codelist/tree/bikes.json"
                },
                {
                    "field": "frame_material",
                    "message": "INVALID-MATERIAL is not a valid option",
                    "code_list": "https://api.cyclesoftware.nl/api/v4/articledata/codelist/frame_material.json"
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
