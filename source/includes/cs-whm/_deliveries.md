# Inbound orders #

Access inbound deliveries and inbound backlog data

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `warehouse`


## Inbound back-log ##

Get a list of goods to be delivered.

| GET parameter | Type    | Description                                                                                       |
|---------------|---------|---------------------------------------------------------------------------------------------------|
| `supplier_id` | integer | If supplied only the data for the specified supplier is given<br/>See common api for supplier-ids |
| `is_assigned` | integer | if 1 only assigned items are returned                                                             |
| `offset`      | integer | Pagination offset. <i class="label label-info">optional</i>                                       |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/warehouse/inbound/backlog.json</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/warehouse/inbound/backlog.json?supplier_id=:supplier_id&is_assigned=1&offset=:offset</h6>
	</div>
</div>

### Properties ###

| Property                                       | Type       | Description                                             |
|------------------------------------------------|------------|---------------------------------------------------------|
| `error`                                        | `boolean`  | `true` when an error occured                            |
| `error_message`                                | `?string`  | Error message if known                                  |
| `data`                                         | `object[]` | Array of backlog items                                  |
| `data[].id`                                    | `integer`  | Unique item id `412855`                                 |
| `data[].supplier_id`                           | `integer`  | Supplier ID `2403`                                      |
| `data[].is_sold_to_customer`                   | `boolean`  | Marked as sold to customer `false`                      |
| `data[].in_transit`                            | `boolean`  | Marked as in transit `false`                            |
| `data[].article_id`                            | `string`   | Article ID `LV106`                                      |
| `data[].barcode`                               | `string`   | Barcode of article `8719812004299`                      |
| `data[].supplier_reference`                    | `string`   | Reference of supplier `7171999`                         |
| `data[].supplier_reference_2`                  | `string`   | Reference of supplier 2 `7171999`                       |
| `data[].delivery_date`                         | `date`     | Expected delivery-date `2022-12-26`                     |
| `data[].original_delivery_date`                | `date`     | Original expected delivery-date `2023-01-02`            |
| `data[].external_remarks`                      | `string`   | Remarks from supplier                                   |
| `data[].internal_remarks`                      | `?string`  | Internal remarks                                        |
| `data[].created_at`                            | `datetime` | Date-time created                                       |
| `data[].modified_at`                           | `datetime` | Date-time modified                                      |
| `data[].assignment`                            | `?object`  | If not null the item is assigned                        |
| `data[].assignment.assigned_to_entity_type_id` | `integer`  | Entity type assignment `20` (see common api)            |
| `data[].assignment.assigned_to_entity_id`      | `integer`  | Entity ID of assignment `564840`                        |
| `data[].assignment.outbound_order_id`          | `integer`  | Assigned outbound order id `440452`                     |
| `data[].assignment.reference`                  | `string`   | Reference of outbound-order `fvs_138443`                |
| `pagination.next_offset`                       | `?integer` | If specified use offset in GET parameter for extra data |



> HTTP request

```http
GET /api/v1/warehouse/inbound/backlog.json HTTP/1.1
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
Content-length: 1330

{
  "error": false,
  "error_message": null,
  "data": [
    {
      "id": 412805,
      "supplier_id": 2403,
      "is_sold_to_customer": false,
      "in_transit": false,
      "article_id": "LV105",
      "barcode": "8719812004282",
      "supplier_reference": "7171648",
      "supplier_reference_2": "7171648",
      "delivery_date": "2022-11-07",
      "original_delivery_date": "2022-11-14",
      "external_remarks": "",
      "internal_remarks": "some text",
      "created_at": "2022-04-21 12:15:56",
      "modified_at": "2022-04-21 12:18:53",
      "assignment": null
    },
    {
      "id": 412843,
      "supplier_id": 2403,
      "is_sold_to_customer": false,
      "in_transit": false,
      "article_id": "LV106",
      "barcode": "8719812004299",
      "supplier_reference": "7171984",
      "supplier_reference_2": "7171984",
      "delivery_date": "2022-10-24",
      "original_delivery_date": "2022-10-31",
      "external_remarks": "BL-412843",
      "internal_remarks": null,
      "created_at": "2022-04-21 12:15:56",
      "modified_at": "2022-04-21 12:18:53",
      "assignment": {
        "assigned_to_entity_type_id": 20,
        "assigned_to_entity_id": 564840,
        "outbound_order_id": 440452,
        "reference": "yourref_138443"
      }
    }
  ],
  "pagination": {
    "next_offset": 2
  }
}
```


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
