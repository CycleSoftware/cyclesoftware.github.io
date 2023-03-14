# Stock #

Access stock data

***Authentication mechanism***

- Basic HTTP Authentication

## Stockinfo ##

Get stock-info for a set of barcodes. The max number of barcodes is 10. If more are supplied remote supplier stock is
not included.

- Scope(s): `e-commerce`

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

| Property                                               | Type       | Description                                                                                                                                                                                                   |
|--------------------------------------------------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `error`                                                | `boolean`  | e.g. `false`                                                                                                                                                                                                  |
| `error_message`                                        | `?string`  | Error message if error is `true`                                                                                                                                                                              |
| `data.result_items`                                    | `object[]` | array of result objects                                                                                                                                                                                       |
| `data.result_items[].barcode`                          | `string`   | e.g. `4026495856010`                                                                                                                                                                                          |
| `data.result_items[].stock_available`                  | `boolean`  | if true, there is stock available within stores                                                                                                                                                               |
| `data.result_items[].delivery_date`                    | `?date`    | expected delivery date from supplier or back-orders / expected stock                                                                                                                                          |
| `data.result_items[].delivery_date_backlog`            | `?date`    | expected delivery date based on back-orders or expected stock                                                                                                                                                 |
| `data.result_items[].stock_supplier`                   | `?boolean` | `true` if supplier has stock, `false` if supplier has no stock, `null` if not checked                                                                                                                         |
| `data.result_items[].stock_quantity`                   | `integer`  | quantity available in stores                                                                                                                                                                                  |
| `data.result_items[].stock_stores`                     | `object[]` | info per store                                                                                                                                                                                                |
| `data.result_items[].stock_stores[].dealer_id`         | `integer`  | store number `1`                                                                                                                                                                                              |
| `data.result_items[].stock_stores[].store_name`        | `string`   | Name of the store `test`                                                                                                                                                                                      |
| `data.result_items[].stock_stores[].store_phone`       | `string`   | Phone of the store `0733030050`                                                                                                                                                                               |
| `data.result_items[].stock_stores[].quantity`          | `integer`  | quantity available including demo `0`                                                                                                                                                                         |
| `data.result_items[].stock_stores[].quantity_demo`     | `integer`  | Quantity of demo models                                                                                                                                                                                       |
| `data.result_items[].stock_stores[].quantity_expected` | `integer`  | Quantity expected from supplier                                                                                                                                                                               |
| `data.result_items[].stock_stores[].delivery_dates`    | `string[]` | Delivery dates expected from supplier. <br/>If back-orders are available the date of back-order will be used.<br/>If objects are not assigned to a back-order and have a delivery date this date will be used |
| `data.result_items[].article_id`                       | `string`   | Article ID in request url                                                                                                                                                                                     |

> HTTP request

```http
GET /app/api/v3/stockinfo/4026495856010/4026495843614/ HTTP/1.1
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

| Property                      | Type       | Description                                     |
|-------------------------------|------------|-------------------------------------------------|
| `error`                       | `boolean`  | e.g. `false`                                    |
| `error_message`               | `?string`  |                                                 |
| `data`                        | `object[]` | Array of objects                                |
| `data[].account_id`           | `integer`  | Account ID of store e.g. `1`                    |
| `data[].store_id`             | `integer`  | ID of the POS store e.g. `1`                    |
| `data[].object_id`            | `integer`  | POS Object ID e.g. `22952`                      |
| `data[].sales_order_id`       | `integer`  | POS order id e.g. `0`                           |
| `data[].brand_name`           | `string`   | Brand name e.g. `ZNEN`                          |
| `data[].article_id`           | `string`   | Article number e.g. `787-25646`                 |
| `data[].barcode`              | `string`   | Barcode e.g. `2200082836636`                    |
| `data[].description`          | `string`   | Object brand + model e.g. `ZNEN Scooter 8N 20"` |
| `data[].frame_id`             | `string`   | Framenumber e.g. `FR121212`                     |
| `data[].purchase_price_cents` | `integer`  | Purchase price cents e.g. `205800`              |
| `data[].dealer_rrp_cents`     | `integer`  | RRP cents e.g. `349900`                         |
| `data[].is_sold_to_customer`  | `boolean`  | Sold indicator e.g. `true`                      |
| `data[].is_demo`              | `boolean`  | Demo indicator e.g. `false`                     |
| `data[].is_used`              | `boolean`  | Used indicator e.g. `false`                     |
| `data[].has_invoice`          | `boolean`  | Has an invoice e.g. `true`                      |
| `data[].stocked_at`           | `?date`    | Date of stocking e.g. `2019-01-24`              |
| `data[].custom_variable_1`    | `string`   | Custom variable e.g. `Some value`               |
| `data[].is_deleted`           | `boolean`  | Is deleted indicator e.g. `false`               |

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
