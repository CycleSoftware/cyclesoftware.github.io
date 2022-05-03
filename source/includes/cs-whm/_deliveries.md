# Inbound deliveries #

Access inbound deliveries data

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `warehouse`

## Inbound delivered items ##

Get a list of delivered inbound goods

| GET parameter | Type    | Description                                                               |
|---------------|---------|---------------------------------------------------------------------------|
| `start_date`  | date    | Start date interval (yyyy-mm-dd) <i class="label label-info">required</i> |
| `end_date`    | date    | Start date interval (yyyy-mm-dd) <i class="label label-info">required</i> |
| `offset`      | integer | Pagination offset. <i class="label label-info">optional</i>               |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/warehouse/inbound/delivered-items.json?start_date=:start_date&end_date=:end_date</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/warehouse/inbound/delivered-items.json?start_date=:start_date&end_date=:end_date&offset=:offset</h6>
	</div>
</div>

> Response

```json
{
  "error": false,
  "error_message": null,
  "data": [
    {
      "article_id": "ART1",
      "barcode": "1000001",
      "datetime_delivered": "2021-01-01 12:00:33",
      "inbound_delivery_id": 10000,
      "inbound_delivery_item_id": 100001,
      "packinglist_number": "PB11",
      "purchase_price_cents": 10099,
      "quantity_missing": 0,
      "quantity_packinglist": 1,
      "quantity_scanned": 0,
      "quantity_stocked": 1,
      "supplier_id": 2113
    },
    {
      "article_id": "ART2",
      "barcode": "1000002",
      "datetime_delivered": "2021-01-01 12:00:33",
      "inbound_delivery_id": 10000,
      "inbound_delivery_item_id": 100002,
      "packinglist_number": "PB11",
      "purchase_price_cents": 10099,
      "quantity_missing": 0,
      "quantity_packinglist": 1,
      "quantity_scanned": 0,
      "quantity_stocked": 0,
      "supplier_id": 2113
    }
  ],
  "pagination": {
    "next_offset": null
  }
}
```
