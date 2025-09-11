# Supplier packing lists #

Get a list of delivered articles with usage of a packinglist.

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `resources`

### Packing list (object)

Properties used in get endpoint.

| Property                           | Type     | Description                                                             |
|------------------------------------|----------|-------------------------------------------------------------------------|
| `supplier_packinglist_id`          | integer  | Packing list ID in Cyclesoftware `2222`                                 |
| `supplier_packinglist_item_id`     | integer  | The ID of this item on the packing list `3456`                          |
| `store_id`                         | integer  | Store ID within account `2`                                             |
| `supplier_id`                      | integer  | The supplier id in Cyclesoftware `117`                                  |
| `supplier_name`                    | string   | Name of the supplier `Aalten`                                           |
| `supplier_order_id`                | integer  | ID of the order where this item was in `10012`                          |
| `employee_id`                      | integer  | ID of the employee in this account that imported this packing list `45` |
| `employee_name`                    | string   | Name of the employee that imported this packing list `Steve`            |
| `barcode`                          | string   | Barcode of the item on the packing list `123456789`                     | 
| `article_id`                       | string   | Supplier article ID of the item `ABC1234`                               |
| `unit_purchase_price_ex_vat_cents` | integer  | Purchase price excluding VAT in eurocents `399`                         |
| `quantity`                         | integer  | Amount of units delivered `3`                                           |
| `stock_object_id`                  | integer  | ID of the stock object this item is assigned to `2335`                  |
| `created_at`                       | datetime | Date the packing list was imported `27-09-2025 11:47`                   |

## Get packing list items
Get all items on packing lists in a configurable period

<div class="api-endpoint">
<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/supplier/packinglists.json</h6>
	</div>
</div>

| GET parameter | Type     | Description                                                   |
|---------------|----------|---------------------------------------------------------------|
| `offset`      | integer  | Offset for pagination `300`                                   |
| `start_date`  | datetime | Start date for querying packing list items `27-09-2025 11:47` |
| `end_date`    | datetime | End date for querying packing list items `27-09-2025 11:47`   |

> HTTP request

```http
GET /api/v1/supplier/packinglists.json?offset=300&start_date=01-01-2025&end_date=27-09-2025 HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 425
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "data": [
      {
        "supplier_packinglist_id": 1837221,
        "supplier_packinglist_item_id": 8477749,
        "store_id": 1,
        "supplier_id": 8939,
        "supplier_name": null,
        "packinglist_number": "Order-2118",
        "supplier_order_id": 0,
        "employee_id": 46933,
        "employee_name": "Sep",
        "barcode": "OBSTB",
        "article_id": "12345",
        "unit_purchase_price_ex_vat_cents": 500,
        "quantity": 2,
        "stock_object_id": null,
        "created_at": "2025-06-07 12:33:45"
      }
    ],
    "pagination": {
      "previous": "https://s01.cyclesoftware.nl/api/v1/supplier/packinglists.json?start_date=01-01-2020&end_date=27-09-2025&offset=100",
      "next": "https://s01.cyclesoftware.nl/api/v1/supplier/packinglists.json?start_date=01-01-2020&end_date=27-09-2025&offset=300"
    }
}
```
