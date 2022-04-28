# Stock #

Access stock data

***Authentication mechanism***

- Basic HTTP Authentication

## Stockinfo ##

Get stock-info for a set of barcodes. The max number of barcodes is 10. If more are supplied remote supplier stock is
not included.

- Scope(s): `ecommerce`

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/v3/stockinfo/:barcode1/:barcode2/../../</h6>
	</div>
</div>

| GET parameter           | Type    | Description                                                                                     |
|-------------------------|---------|-------------------------------------------------------------------------------------------------|
| `only_supplier_stock`   | integer | if 1 stock in stores is ignored <i class="label label-info">optional</i>                        |
| `only_supplier_id`      | integer | If supplied only the stock of this supplier is checked <i class="label label-info">optional</i> |
| `remote_supplier_check` | integer | If 0, no remote supplier checks are performed <i class="label label-info">optional</i>          |

### Properties ###

| Property                                               | Type       | Nullable | Description                                                                           |
|--------------------------------------------------------|------------|----------|---------------------------------------------------------------------------------------|
| `error`                                                | `boolean`  | `false`  | e.g. `false`                                                                          |
| `error_message`                                        | `string`   | `false`  | e.g. ``                                                                               |
| `data.result_items`                                    | `array`    | `false`  | array of result objects                                                               |
| `data.result_items[].barcode`                          | `string`   | `false`  | e.g. `4026495856010`                                                                  |
| `data.result_items[].stock_available`                  | `boolean`  | `false`  | if true, there is stock available within stores                                       |
| `data.result_items[].delivery_date`                    | `date`     | `true`   | expected delivery date from supplier or back-orders / expected stock                  |
| `data.result_items[].delivery_date_backlog`            | `date`     | `true`   | expected delivery date based on back-orders or expected stock                         |
| `data.result_items[].stock_supplier`                   | `boolean`  | `true`   | `true` if supplier has stock, `false` if supplier has no stock, `null` if not checked |
| `data.result_items[].stock_quantity`                   | `integer`  | `false`  | quantity available in stores                                                          |
| `data.result_items[].stock_stores`                     | `array`    | `false`  | info per store                                                                        |
| `data.result_items[].stock_stores[].dealer_id`         | `integer`  | `false`  | store number `1`                                                                      |
| `data.result_items[].stock_stores[].store_name`        | `string`   | `false`  | Name of the store `test`                                                              |
| `data.result_items[].stock_stores[].store_phone`       | `string`   | `false`  | Phone of the store `0733030050`                                                       |
| `data.result_items[].stock_stores[].quantity`          | `integer`  | `false`  | quantity available including demo `0`                                                 |
| `data.result_items[].stock_stores[].quantity_demo`     | `integer`  | `false`  | Quantity of demo models                                                               |
| `data.result_items[].stock_stores[].quantity_expected` | `integer`  | `false`  | Quantity expected from supplier                                                       |
| `data.result_items[].stock_stores[].delivery_dates`    | `string[]` | `false`  | Delivery dates expected from supplier                                                 |
| `data.result_items[].article_id`                       | `string`   | `false`  | Article ID in request url                                                             |

> HTTP request

```http
GET /app/api/v3/stockinfo/4026495856010/4026495843614/ HTTP/1.1
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
Content-length: 1574

{
    "error": false,
    "error_message": "",
    "data": {
        "result_items": [
            {
                "barcode": "4026495843614",
                "stock_available": true,
                "delivery_date": null,
                "stock_supplier": null,
                "stock_quantity": 3,
                "stock_stores": [
                    {
                        "dealer_id": 1,
                        "store_name": "test",
                        "store_phone": "0733030050",
                        "quantity": 3,
                        "quantity_demo": 0,
                        "quantity_expected": 0,
                        "delivery_dates": []
                    }
                ],
                "article_id": "4026495843614"
            },
            {
                "barcode": "4026495843690",
                "stock_available": true,
                "delivery_date": "01-01-2022",
                "delivery_date_backlog": "01-01-2022",
                "stock_supplier": null,
                "stock_quantity": 3,
                "stock_stores": [
                    {
                        "dealer_id": 1,
                        "store_name": "test",
                        "store_phone": "0733030050",
                        "quantity": 3,
                        "quantity_demo": 0,
                        "quantity_expected": 1,
                        "delivery_dates": [
                            "01-01-2022"
                        ]
                    }
                ],
                "article_id": "4026495843614"
            },
            {
                "barcode": "4026495856010",
                "stock_available": true,
                "stock_quantity": 0,
                "delivery_date": null,
                "stock_supplier": true,
                "stock_stores": [
                    {
                        "dealer_id": 1,
                        "store_name": "test",
                        "store_phone": "0733030050",
                        "quantity": 0,
                        "quantity_demo": 0,
                        "quantity_expected": 0,
                        "delivery_dates": []
                    }
                ],
                "article_id": "4026495856010"
            }
        ]
    }
}
```

## Stock list ##

Get a list of stocked objects with status available or pro-forma sold.

- Scope(s): `stock-export`

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/stock/pos-items.json</h6>
	</div>
</div>

### Properties ###

| Property                    | Type      | Nullable | Description                                     |
|-----------------------------|-----------|----------|-------------------------------------------------|
| error                       | `boolean` | `false`  | e.g. `false`                                    |
| error_message               | `null`    | `true`   |                                                 |
| data                        | `array`   | `false`  |                                                 |
| data[].account_id           | `integer` | `false`  | Account ID of store e.g. `1`                    |
| data[].store_id             | `integer` | `false`  | ID of the POS store e.g. `1`                    |
| data[].object_id            | `integer` | `false`  | POS Object ID e.g. `22952`                      |
| data[].sales_order_id       | `integer` | `false`  | POS order id e.g. `0`                           |
| data[].brand_name           | `string`  | `false`  | Brand name e.g. `ZNEN`                          |
| data[].article_id           | `string`  | `false`  | Article number e.g. `787-25646`                 |
| data[].barcode              | `string`  | `false`  | Barcode e.g. `2200082836636`                    |
| data[].description          | `string`  | `false`  | Object brand + model e.g. `ZNEN Scooter 8N 20"` |
| data[].frame_id             | `string`  | `false`  | Framenumber e.g. ``                             |
| data[].purchase_price_cents | `integer` | `false`  | Purchase price cents e.g. `205800`              |
| data[].dealer_rrp_cents     | `integer` | `false`  | RRP cents e.g. `349900`                         |
| data[].is_sold_to_customer  | `boolean` | `false`  | Sold indicator e.g. `true`                      |
| data[].is_demo              | `boolean` | `false`  | Demo indicator e.g. `false`                     |
| data[].is_used              | `boolean` | `false`  | Used indicator e.g. `false`                     |
| data[].has_invoice          | `boolean` | `false`  | Has an invoice e.g. `true`                      |
| data[].stocked_at           | `date`    | `true`   | Date of stocking e.g. `2019-01-24`              |
| data[].custom_variable_1    | `string`  | `false`  | Custom variable e.g. ``                         |
| data[].is_deleted           | `boolean` | `false`  | Is deleted indicator e.g. `false`               |


> Response

```json
{
  "error": false,
  "error_message": null,
  "data": [
    {
      "account_id": 1,
      "store_id": 1,
      "object_id": 21016,
      "sales_order_id": 0,
      "supplier": "Votani",
      "article_id": "99.Y2634.Q14",
      "barcode": "2200054202292",
      "description": "Votani X2 Mid Motor",
      "frame_id": "",
      "purchase_price_cents": 0,
      "dealer_rrp_cents": 130000,
      "is_sold_to_customer": true,
      "is_demo": false,
      "is_used": false,
      "has_invoice": true,
      "stocked_at": "2015-11-25",
      "custom_variable_1": "",
      "is_deleted": false
    },
    {
      "account_id": 1,
      "store_id": 1,
      "object_id": 22952,
      "sales_order_id": 0,
      "supplier": "ZNEN",
      "article_id": "787-25646",
      "barcode": "2200082836636",
      "description": "ZNEN Scooter 8N 20\"",
      "frame_id": "",
      "purchase_price_cents": 205800,
      "dealer_rrp_cents": 349900,
      "is_sold_to_customer": true,
      "is_demo": false,
      "is_used": false,
      "has_invoice": true,
      "stocked_at": "2019-01-24",
      "custom_variable_1": "",
      "is_deleted": false
    }
  ]
}
```
