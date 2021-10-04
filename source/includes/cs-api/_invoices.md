# Invoices #

Access invoice data

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `salesdata`

## Unbooked invoices ##
Get a list of unbooked sales transactions / invoices.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/invoices/unbooked.json</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/invoices/unbooked.json?offset=1000</h6>
	</div>
</div>

| GET parameter               | Type      | Description                                                                                                          |
|-------------------------|-----------|----------------------------------------------------------------------------------------------------------------------|
|`offset`                  | integer    | Pagination offset. <i class="label label-info">optional</i>                                                                                                          |


> HTTP request

```http
GET /api/v1/invoices/unbooked.json HTTP/1.1
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
Content-length: 722

{
  "data": [
    {
      "created_at": "2009-10-21 00:00:00",
      "customer_id": 0,
      "modified_at": "2016-06-27 09:12:39",
      "sales_order_id": null,
      "sales_transaction_number": 20171235,
      "store_id": 1,
      "total_amount_cents": 12500,
      "transaction_date": "2009-10-21",
      "unpayed_amount_cents": 12500
    },
    {
      "created_at": "2009-10-21 00:00:00",
      "customer_id": 0,
      "modified_at": "2016-06-27 09:12:39",
      "sales_order_id": null,
      "sales_transaction_number": 20001,
      "store_id": 1,
      "total_amount_cents": 12500,
      "transaction_date": "2009-10-21",
      "unpayed_amount_cents": 12500
    }
  ],
  "pagination": {
    "next_offset": null
  }
}
```
