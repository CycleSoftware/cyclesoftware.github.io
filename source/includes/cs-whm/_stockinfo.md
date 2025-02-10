# Stock #

Access stock info for warehouse

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `warehouse`

## Stock-info ##

Get a list of stock items released for shipment

| GET parameter                               | Type      | Description                                                                                                                      |
|---------------------------------------------|-----------|----------------------------------------------------------------------------------------------------------------------------------|
| `stock_items`                               | `integer` | if set to 1 details about the stock items is provided <i class="label label-info">optional</i>                                   |
| `no_remote_supplier_check`                  | `integer` | if set to 1 no remote supplier checks are included <i class="label label-info">optional</i>                                      |
| `only_supplier_stock`                       | `integer` | if set to 1 only remote supplier stock is checked, store and warehouse stock is ignored <i class="label label-info">optional</i> |
| `only_supplier_id`                          | `integer` | if a supplier_id is given only this supplier will be included for supplier stock checks <i class="label label-info">optional</i> |
| `remote_supplier_check_if_not_in_warehouse` | `integer` | if set to 1 supplier check will always be checked there is no stock in warehouse <i class="label label-info">optional</i>        |
| `always_remote_supplier_check`              | `integer` | if set to 1 supplier check will always be checked <i class="label label-info">optional</i>                                       |

| POST parameter | Type       | Description       |
|----------------|------------|-------------------|
| `barcodes`     | `string[]` | array of barcodes |

### Properties ###

| Property                                                     | Type       | Description                                                                                                                                          |
|--------------------------------------------------------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| `error`                                                      | `boolean`  | true if errors occurred                                                                                                                              |
| `error_message`                                              | `?string`  | Error message if occurred                                                                                                                            |
| `data.status`                                                | `boolean`  | true if no errors occurred                                                                                                                           |
| `data.result_items`                                          | `object[]` | Result per requested barcode                                                                                                                         |
| `data.result_items[].barcode`                                | `string`   | Article barcode                                                                                                                                      |
| `data.result_items[].stock_available`                        | `boolean`  | Overall status whether stock is available                                                                                                            |
| `data.result_items[].delivery_date`                          | `?date`    | expected delivery date from supplier                                                                                                                 |
| `data.result_items[].delivery_date_supplier`                 | `?date`    | expected delivery date from supplier                                                                                                                 |
| `data.result_items[].delivery_date_backlog`                  | `?date`    | expected delivery date from registered backlog orders supplier                                                                                       |
| `data.result_items[].stock_supplier`                         | `?boolean` | true if stock available at supplier, null if not checked                                                                                             |
| `data.result_items[].stock_quantity`                         | `integer`  | available quantity within stores+warehouse (new+demo+used+rental)                                                                                    |
| `data.result_items[].stock_quantity_stores`                  | `integer`  | available quantity within stores                                                                                                                     |
| `data.result_items[].stock_quantity_warehouse`               | `integer`  | available quantity within warehouse                                                                                                                  |
| `data.result_items[].stock_stores`                           | `object[]` | array with stock info per store                                                                                                                      |
| `data.result_items[].stock_stores[].dealer_id`               | `integer`  | dealer-id of store                                                                                                                                   |
| `data.result_items[].stock_stores[].store_name`              | `string`   | name of store                                                                                                                                        |
| `data.result_items[].stock_stores[].store_phone`             | `string`   | phone number of store                                                                                                                                |
| `data.result_items[].stock_stores[].quantity`                | `integer`  | Quantity of `new`+`demo` models (this is different in POS implementation, quantity of objects have priority over article stock if both are present)) |
| `data.result_items[].stock_stores[].quantity_new`            | `integer`  | Quantity of new models available                                                                                                                     |
| `data.result_items[].stock_stores[].quantity_demo`           | `integer`  | Quantity of demo models available                                                                                                                    |
| `data.result_items[].stock_stores[].quantity_used`           | `integer`  | Quantity of used models available                                                                                                                    |
| `data.result_items[].stock_stores[].quantity_rental`         | `integer`  | Quantity of rental models available                                                                                                                  |
| `data.result_items[].stock_stores[].quantity_expected`       | `integer`  | Quantity expected from supplier                                                                                                                      |
| `data.result_items[].stock_stores[].objects`                 | `object[]` | List of stock objects, empty for articles                                                                                                            | 
| `data.result_items[].stock_stores[].objects[].object_id`     | `integer`  | Object ID e.g. `10001`                                                                                                                               |
| `data.result_items[].stock_stores[].objects[].status`        | `string`   | Status of object e.g. `new`, `demo`, `rental`, `expected`                                                                                            |
| `data.result_items[].stock_stores[].objects[].delivery_date` | `?date`    | Delivery date if known and status `expected` e.g. `19-02-2025`                                                                                       |
| `data.result_items[].supplier_id`                            | `?string`  | used supplier_id in request                                                                                                                          |
| `data.result_items[].article_id`                             | `string`   | used "barcode" in request e.g. `8719461035781`                                                                                                       |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/whm/stockinfo/:barcode1/:barcode2/../../</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/whm/stockinfo/:barcode1/:barcode2/../../?stock_items={0,1}</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/whm/stockinfo/:barcode1/:barcode2/../../?no_remote_supplier_check={0,1}</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/whm/stockinfo/:barcode1/:barcode2/../../?only_supplier_stock={0,1}</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/whm/stockinfo/:barcode1/:barcode2/../../?only_supplier_id=:supplier_id</h6>
	</div>
</div>


<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/app/api/whm/stockinfo/</h6>
	</div>
</div>


> Response

```json
{
  "error": false,
  "error_message": "",
  "data": {
    "status": true,
    "result_items": [
      {
        "barcode": "8719461035781",
        "stock_available": true,
        "delivery_date": null,
        "delivery_date_supplier": null,
        "delivery_date_backlog": null,
        "stock_supplier": null,
        "stock_quantity": 3,
        "stock_quantity_stores": 3,
        "stock_quantity_warehouse": 0,
        "stock_stores": [
          {
            "dealer_id": 791825,
            "store_name": "Utrecht",
            "store_phone": "999-11223344",
            "quantity": 1,
            "quantity_new": 0,
            "quantity_demo": 1,
            "quantity_used": 0,
            "quantity_rental": 0,
            "quantity_expected": 0,
            "objects": [
              {
                "object_id": 1075366,
                "status": "demo"
              }
            ]
          },
          {
            "dealer_id": 857361,
            "store_name": "Breda",
            "store_phone": "999-11223344",
            "quantity": 2,
            "quantity_new": 1,
            "quantity_demo": 1,
            "quantity_used": 0,
            "quantity_rental": 0,
            "quantity_expected": 1,
            "objects": [
              {
                "object_id": 1039262,
                "status": "demo"
              },
              {
                "object_id": 1101358,
                "status": "new"
              },
              {
                "object_id": 343444,
                "status": "expected",
                "delivery_date": "01-01-2025"
              }
            ]
          }
        ],
        "supplier_id": null,
        "article_id": "8719461035781"
      },
      {
        "barcode": "8719461035782",
        "stock_available": false,
        "delivery_date": "01-01-2022",
        "delivery_date_supplier": "01-05-2022",
        "delivery_date_backlog": "01-01-2022",
        "stock_supplier": false,
        "stock_quantity": 0,
        "stock_quantity_stores": 0,
        "stock_quantity_warehouse": 0,
        "stock_stores": [],
        "supplier_id": null,
        "article_id": "8719461035782"
      }
    ]
  }
}
```

## Stock list Warehouse ##

Get a list of objects in warehouse

### Properties ###

| Property                                  | Type        | Description                                                                             |
|-------------------------------------------|-------------|-----------------------------------------------------------------------------------------|
| `error`                                   | `boolean`   | `true` if error occurred                                                                |
| `error_message`                           | `?string`   | Error if occurred                                                                       |
| `data`                                    | `object[]`  | array of objects                                                                        |
| `data[].stock_item_id`                    | `integer`   | Object ID within warehouse `325817`                                                     |
| `data[].outbound_order_id`                | `integer`   | Outbound order ID                                                                       |
| `data[].supplier`                         | `string`    | Supplier name                                                                           |
| `data[].article_id`                       | `string`    | Article number `735-18460`                                                              |
| `data[].barcode`                          | `string`    | Barcode `4063518126705`                                                                 |
| `data[].description`                      | `string`    | Description of article `Ravenna E8F Herenfiets 28" grey 60 cm diamant`                  |
| `data[].frame_id`                         | `string`    | Framenumber `AA01148291`                                                                |
| `data[].purchase_price_cents`             | `integer`   | Purchase price in cents                                                                 |
| `data[].purchase_price_cents_packinglist` | `integer`   | Purchase price in cents from last packinglist                                           |
| `data[].dealer_rrp_cents`                 | `integer`   | RRP in cents                                                                            |
| `data[].claimed_for_account_id`           | `?integer`  | If claimed the account_id                                                               |
| `data[].claimed_for_store_id`             | `?integer`  | If claimed the store_id                                                                 |
| `data[].is_blocked_for_claiming`          | `boolean`   | `true` if blocked for claiming                                                          |
| `data[].is_claimed_for_obo`               | `boolean`   | `true` if claimed for outbound order                                                    |
| `data[].is_sold_to_customer`              | `boolean`   | `true` if sold to a customer                                                            |
| `data[].is_shipped`                       | `boolean`   | `true` if shipped                                                                       |
| `data[].is_deleted`                       | `boolean`   | `true` if item was deleted                                                              |
| `data[].stocked_at`                       | `datetime`  | Datetime stocked `2021-10-22 11:33:03`                                                  |
| `data[].shipped_at`                       | `?datetime` | Datetime shipped                                                                        |
| `data[].custom_variable_1`                | `string`    | Custom variable from article                                                            |
| `data[].custom_variable_2`                | `string`    | Custom variable from article                                                            |
| `data[].custom_variable_3`                | `string`    | Custom variable from article                                                            |
| `data[].custom_variable_4`                | `string`    | Custom variable from article                                                            |
| `data[].custom_variable_5`                | `string`    | Custom variable from article                                                            |
| `data[].warehouse_group_name`             | `?string`   | Warehouse group name if set e.g. `Hall`                                                 |
| `data[].warehouse_location`               | `?string`   | Warehouse location if not shipped `B-1-1`                                               |
| `pagination.next_url`                     | `?string`   | `null` if all data processed. Contains URL to next result set if more data is available |
### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v2/warehouse/stock/items.json</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v2/warehouse/stock/items.json?offset=:offset</h6>
	</div>
</div>

> Response

```json
{
  "error": false,
  "error_message": null,
  "data": [
    {
      "stock_item_id": 109993,
      "outbound_order_id": 315254,
      "supplier": "Leopard",
      "article_id": "593005",
      "barcode": "8717931438117",
      "description": "Leopard Tess 24 inch 2019 M24-39 Zwart Mat",
      "frame_id": "17017456",
      "purchase_price_cents": 40900,
      "purchase_price_cents_packinglist": 40900,
      "dealer_rrp_cents": 41900,
      "claimed_for_account_id": 1000,
      "claimed_for_store_id": 13,
      "is_blocked_for_claiming": false,
      "is_claimed_for_obo": true,
      "is_sold_to_customer": true,
      "is_shipped": false,
      "is_deleted": false,
      "stocked_at": "2018-04-24 08:53:20",
      "shipped_at": "2021-04-13 07:59:29",
      "custom_variable_1": "Custom var 1",
      "custom_variable_2": "Custom var 2",
      "custom_variable_3": "Custom var 3",
      "custom_variable_4": "Custom var 4",
      "custom_variable_5": "Custom var 5",
      "warehouse_group_name": "Hall",
      "warehouse_location": "A-1-1"
    },
    {
      "stock_item_id": 203013,
      "outbound_order_id": 376797,
      "supplier": "Gazelle",
      "article_id": "G1539",
      "barcode": "8717231346426",
      "description": "Orange C8 HMB H8",
      "frame_id": "61380279",
      "purchase_price_cents": 279900,
      "purchase_price_cents_packinglist": 279900,
      "dealer_rrp_cents": 289900,
      "claimed_for_account_id": 1000,
      "claimed_for_store_id": 23,
      "is_blocked_for_claiming": false,
      "is_claimed_for_obo": true,
      "is_sold_to_customer": false,
      "is_shipped": true,
      "is_deleted": true,
      "stocked_at": "2020-06-11 10:59:05",
      "shipped_at": "2021-10-15 10:03:09",
      "custom_variable_1": "Custom var 1",
      "custom_variable_2": "Custom var 2",
      "custom_variable_3": "Custom var 3",
      "custom_variable_4": "Custom var 4",
      "custom_variable_5": "Custom var 5",
      "warehouse_group_name": null,
      "warehouse_location": null
    }
  ],
  "pagination": {
    "next_url": null
  }
}
```

## Stock list POS ##

Get a list of stocked objects in POS

### Properties ###

| Property                                  | Type       | Description                                                                              |
|-------------------------------------------|------------|------------------------------------------------------------------------------------------|
| `error`                                   | `boolean`  | `true` if error occurred e.g. `false`                                                    |
| `error_message`                           | `?string`  | Error message or null                                                                    |
| `data[].account_id`                       | `integer`  | Account ID of store `5393`                                                               |
| `data[].store_id`                         | `integer`  | ID of the POS store `2`                                                                  |
| `data[].object_id`                        | `integer`  | POS Object ID `20648`                                                                    |
| `data[].warehouse_stock_item_id`          | `?integer` | Item ID in warehouse e.g `2220648` (only for WHM dealers), registered since march 2024   |
| `data[].sales_order_id`                   | `integer`  | POS order id `1000`                                                                      |
| `data[].supplier`                         | `string`   | Supplier name `Gazelle`                                                                  |
| `data[].article_id`                       | `string`   | Article number `A1935`                                                                   |
| `data[].barcode`                          | `string`   | Barcode `8717231254776`                                                                  |
| `data[].description`                      | `string`   | Description `Gazelle Eclipse C8 LTD`                                                     |
| `data[].frame_id`                         | `string`   | Framenumber `60516151`                                                                   |
| `data[].purchase_price_cents`             | `integer`  | Purchase price in cents `50980`                                                          |
| `data[].purchase_price_cents_packinglist` | `integer`  | Purchase price in cents from last packinglist `50980`                                    |
| `data[].dealer_rrp_cents`                 | `integer`  | RRP in cents `94900`                                                                     |
| `data[].is_sold_to_customer`              | `boolean`  | `true` if sold to customer                                                               |
| `data[].is_demo`                          | `boolean`  | `true` if marked as demo                                                                 |
| `data[].has_invoice`                      | `boolean`  | `true` if invoiced                                                                       |
| `data[].stocked_at`                       | `date`     | Custom variable from article                                                             |
| `data[].custom_variable_1`                | `string`   | Custom variable from article                                                             |
| `data[].custom_variable_2`                | `string`   | Custom variable from article                                                             |
| `data[].custom_variable_3`                | `string`   | Custom variable from article                                                             |
| `data[].custom_variable_4`                | `string`   | Custom variable from article                                                             |
| `data[].custom_variable_5`                | `string`   | Custom variable from article                                                             |
| `data[].is_deleted`                       | `boolean`  | Item is deleted                                                                          |
| `data[].is_rental`                        | `boolean`  | If rental object `true`                                                                  |
| `data[].is_used`                          | `boolean`  | `true` if not a new object                                                               |
| `pagination.next_url`                     | `?string`  | `null` if all data processed. Contains URL to next result set if more data is availabile |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v2/warehouse/stock/pos-items.json</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v2/warehouse/stock/pos-items.json?token=:token</h6>
	</div>
</div>


> Response

```json
{
  "error": false,
  "error_message": null,
  "data": [
    {
      "account_id": 1000,
      "store_id": 6,
      "object_id": 1076,
      "warehouse_stock_item_id": null,
      "sales_order_id": 0,
      "supplier": "Batavus",
      "article_id": "BE100086",
      "barcode": "8713568256155",
      "description": "Batavus STREAM",
      "frame_id": "BA5169351",
      "purchase_price_cents": 219900,
      "purchase_price_cents_packinglist": 219900,
      "dealer_rrp_cents": 259900,
      "is_sold_to_customer": false,
      "is_demo": true,
      "has_invoice": false,
      "stocked_at": "2015-12-08",
      "custom_variable_1": "Custom var 1",
      "custom_variable_2": "Custom var 2",
      "custom_variable_3": "Custom var 3",
      "custom_variable_4": "Custom var 4",
      "custom_variable_5": "Custom var 5",
      "is_deleted": false,
      "is_used": false,
      "is_rental": false
    },
    {
      "account_id": 1000,
      "store_id": 2,
      "object_id": 4673,
      "warehouse_stock_item_id": null,
      "sales_order_id": 0,
      "supplier": "Gazelle",
      "article_id": "A0828",
      "barcode": "8717231240205",
      "description": "Gazelle Orange C8 Hm",
      "frame_id": "60467933",
      "purchase_price_cents": 190000,
      "purchase_price_cents_packinglist": 190000,
      "dealer_rrp_cents": 210000,
      "is_sold_to_customer": false,
      "is_demo": true,
      "has_invoice": false,
      "stocked_at": "2016-02-03",
      "custom_variable_1": "Custom var 1",
      "custom_variable_2": "Custom var 2",
      "custom_variable_3": "Custom var 3",
      "custom_variable_4": "Custom var 4",
      "custom_variable_5": "Custom var 5",
      "is_deleted": false,
      "is_used": true,
      "is_rental": true
    }
  ],
  "pagination": {
    "next_url": "https://api.cyclesoftware.nl/api/v2/warehouse/stock/pos-items.json?token=1243"
  }
}
```
