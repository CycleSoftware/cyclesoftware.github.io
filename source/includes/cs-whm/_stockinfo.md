# Stock #

Access stock info for warehouse

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `warehouse`

## Stock-info ##

Get a list of stock items released for shipment

| GET parameter               | Type      | Description                                                                                                          |
|-------------------------|-----------|----------------------------------------------------------------------------------------------------------------------|                                                                                                       |
|`stock_items`  | `integer` | if set to 1 details about the stock items is provided <i class="label label-info">optional</i> |
|`no_remote_supplier_check`  | `integer`  | if set to 1 no remote supplier checks are included <i class="label label-info">optional</i> |
|`only_supplier_stock`  | `integer` | if set to 1 only remote supplier stock is checked, store and warehouse stock is ignored <i class="label label-info">optional</i> |
|`only_supplier_id`  | `integer` | if a supplier_id is given only this supplier will be included for supplier stock checks <i class="label label-info">optional</i> |
                                                                                                   

| POST parameter               | Type      | Description                                                                                                          |
|-------------------------|-----------|----------------------------------------------------------------------------------------------------------------------|                                                                                                       |
|`barcodes`                  | `array`    | array of barcodes     |


### Properties ###

| Property                                         | Type              | Nullable        | Description                    |
| ------------------------------------------------ | ----------------- | --------------- | ------------------------------ |
| `error`                                            | `boolean` | `false` | true if errors occurred            |
| `error_message`                                    | `string`  | `false` | Error message if occurred              |
| `data.status`                                      | `boolean` | `false` | true if no errors occurred           |
| `data.result_items`                                | `array`   | `false` | Result per requested barcode                               |
| `data.result_items[].barcode`                      | `string`  | `false` | Article barcode   |
| `data.result_items[].stock_available`              | `boolean` | `false` | Overall status whether stock is available            |
| `data.result_items[].delivery_date`                | `date`    | `true`  | expected delivery date from supplier                               |
| `data.result_items[].delivery_date_supplier`       | `date`    | `true`  | expected delivery date from supplier                               |
| `data.result_items[].delivery_date_backlog`       | `date`    | `true`  | expected delivery date from registered backlog orders supplier                               |
| `data.result_items[].stock_supplier`               | `boolean`    | `true`  | true if stock available at supplier, null if not checked                               |
| `data.result_items[].stock_quantity`               | `integer` | `false` | available quantity within stores+warehouse               |
| `data.result_items[].stock_quantity_stores`        | `integer` | `false` | available quantity within stores               |
| `data.result_items[].stock_quantity_warehouse`     | `integer` | `false` | available quantity within warehouse               |
| `data.result_items[].stock_stores`                 | `array`   | `false` | array with stock info per store                               |
| `data.result_items[].stock_stores[].dealer_id`     | `integer` | `false` | dealer-id of store         |
| `data.result_items[].stock_stores[].store_name`    | `string`  | `false` | name of store    |
| `data.result_items[].stock_stores[].store_phone`   | `string`  | `false` | phone number of store |
| `data.result_items[].stock_stores[].quantity`      | `integer` | `false` | quantity including demo models available               |
| `data.result_items[].stock_stores[].quantity_demo` | `integer` | `false` | quantity of demo models available              |
| `data.result_items[].supplier_id`                  | `string`    | `true`  | used supplier_id in request                               |
| `data.result_items[].article_id`                   | `string`  | `false` | used "barcode" in request e.g. `8719461035781`   |


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
        "stock_quantity": 1,
        "stock_quantity_stores": 1,
        "stock_quantity_warehouse": 0,
        "stock_stores": [
          {
            "dealer_id": 791825,
            "store_name": "Ridderkerk",
            "store_phone": "010-1234567",
            "quantity": 1,
            "quantity_demo": 1
          },
          {
            "dealer_id": 857361,
            "store_name": "Breda",
            "store_phone": "010-1234567",
            "quantity": 1,
            "quantity_demo": 1
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

| Property                       | Type               | Nullable        | Description                                                       |
| ------------------------------ | ------------------ | --------------- | ----------------------------------------------------------------- |
| `error`                          | `boolean`  | `false` | `true` if error occurred                                             |
| `error_message`                  | `null`     | `true`  | Error if occurred                                                                  |
| `data`                           | `array`    | `false` | array of objects                                                                  |
| `data[].stock_item_id`           | `integer`  | `false` | Object ID within warehouse `325817`                                             |
| `data[].outbound_order_id`       | `integer`  | `false` | Outbound order ID                                                  |
| `data[].supplier`                | `string`   | `false` | Supplier name                                               |
| `data[].article_id`              | `string`   | `false` | Article number `735-18460`                                          |
| `data[].barcode`                 | `string`   | `false` | Barcode `4063518126705`                                      |
| `data[].description`             | `string`   | `false` | Description of article `Ravenna E8F Herenfiets 28" grey 60 cm diamant` |
| `data[].frame_id`                | `string`   | `false` | Framenumber `AA01148291`                                         |
| `data[].purchase_price_cents`    | `integer`  | `false` | Purchase price in cents                                                  |
| `data[].dealer_rrp_cents`        | `integer`  | `false` | RRP in cents                                             |
| `data[].claimed_for_account_id`  | `integer`     | `true`  | If claimed the account_id                                                                 |
| `data[].claimed_for_store_id`    | `integer`     | `true`  | If claimed the store_id                                                                  |
| `data[].is_blocked_for_claiming` | `boolean`  | `false` | `true` if blocked for claiming                                              |
| `data[].is_claimed_for_obo`      | `boolean`  | `false` | `true` if claimed for outbound order                                              |
| `data[].is_sold_to_customer`     | `boolean`  | `false` | `true` if sold to a customer                                             |
| `data[].is_shipped`              | `boolean`  | `false` | `true` if shipped                                              |
| `data[].stocked_at`              | `datetime` | `false` | Datetime stocked `2021-10-22 11:33:03`                                |
| `data[].shipped_at`              | `datetime`     | `true`  | Datetime shipped                                                                   |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/warehouse/stock/items.json</h6>
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
      "dealer_rrp_cents": 41900,
      "claimed_for_account_id": 1000,
      "claimed_for_store_id": 13,
      "is_blocked_for_claiming": false,
      "is_claimed_for_obo": true,
      "is_sold_to_customer": true,
      "is_shipped": true,
      "stocked_at": "2018-04-24 08:53:20",
      "shipped_at": "2021-04-13 07:59:29"
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
      "dealer_rrp_cents": 289900,
      "claimed_for_account_id": 1000,
      "claimed_for_store_id": 23,
      "is_blocked_for_claiming": false,
      "is_claimed_for_obo": true,
      "is_sold_to_customer": false,
      "is_shipped": true,
      "stocked_at": "2020-06-11 10:59:05",
      "shipped_at": "2021-10-15 10:03:09"
    }
  ]
}
```

## Stock list POS ##

Get a list of stocked objects in POS

### Properties ###

| Property                    | Type              | Nullable        | Description                           |
| --------------------------- | ----------------- | --------------- | ------------------------------------- |
| `error`                       | `boolean` | `false` | e.g. `false`                  |
| `error_message`               | `null`    | `true`  |                                       |
| `data`                        | `array`   | `false` |                                       |
| `data[].account_id`           | `integer` | `false` | Account ID of store `5393`                   |
| `data[].store_id`             | `integer` | `false` | ID of the POS store `2`                      |
| `data[].object_id`            | `integer` | `false` | POS Object ID `20648`                  |
| `data[].sales_order_id`       | `integer` | `false` | POS order id `1000`                      |
| `data[].supplier`             | `string`  | `false` | Supplier name `Gazelle`                |
| `data[].article_id`           | `string`  | `false` | Article number `A1935`                  |
| `data[].barcode`              | `string`  | `false` | Barcode `8717231254776`          |
| `data[].description`          | `string`  | `false` | Description `Gazelle Eclipse C8 LTD` |
| `data[].frame_id`             | `string`  | `false` | Framenumber `60516151`               |
| `data[].purchase_price_cents` | `integer` | `false` | Purchase price in cents `50980`                  |
| `data[].dealer_rrp_cents`     | `integer` | `false` | RRP in cents `94900`                  |
| `data[].is_sold_to_customer`  | `boolean` | `false` | `true` if sold to customer                  |
| `data[].is_demo`              | `boolean` | `false` | `true` if marked as demo            |
| `data[].has_invoice`          | `boolean` | `false` | `true` if invoiced                  |
| `data[].stocked_at`           | `date`    | `false` | Date of stock            `|


### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/warehouse/stock/pos-items.json</h6>
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
      "sales_order_id": 0,
      "supplier": "Batavus",
      "article_id": "BE100086",
      "barcode": "8713568256155",
      "description": "Batavus STREAM",
      "frame_id": "BA5169351",
      "purchase_price_cents": 219900,
      "dealer_rrp_cents": 259900,
      "is_sold_to_customer": false,
      "is_demo": true,
      "has_invoice": false,
      "stocked_at": "2015-12-08"
    },
    {
      "account_id": 1000,
      "store_id": 2,
      "object_id": 4673,
      "sales_order_id": 0,
      "supplier": "Gazelle",
      "article_id": "A0828",
      "barcode": "8717231240205",
      "description": "Gazelle Orange C8 Hm",
      "frame_id": "60467933",
      "purchase_price_cents": 190000,
      "dealer_rrp_cents": 210000,
      "is_sold_to_customer": false,
      "is_demo": true,
      "has_invoice": false,
      "stocked_at": "2016-02-03"
    }
  ]
}
```
