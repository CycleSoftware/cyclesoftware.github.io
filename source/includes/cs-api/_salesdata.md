# Sales data #

Access sales data

***Authentication mechanism***

- Basic HTTP Authentication
- Scopes: `sales-export`

## Sales transactions ##

Get sales transactions within interval of specified date field (max 31 days).
By default the book-date is used.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/salesdata/json/:start_date/:end_date/</h6>
	</div>
</div>
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/salesdata/json/:start_date/:end_date/?date_field=datetime_modified</h6>
	</div>
</div>

| URI parameter | Type      | Description                                                                                                                                              |
|---------------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `start_date`  | `date`    | end date e.g. 2020-01-01                                                                                                                                 |
| `end_date`    | `date`    | end date e.g. 2020-01-01                                                                                                                                 |

| GET parameter | Type     | Description                                                                                                                                                 |
|---------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `date_field`  | `string` | `kassadatum` (default) interval as booked date<br/> `datetime_modified` interval as modification dates<br/>`factuurdatum` interval as invoice proforma date |

## Pro-forma invoices ##

Get a list of proforma sales transactions / invoices.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/invoices/proforma.json</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/invoices/proforma.json?offset=1000</h6>
	</div>
</div>

| GET parameter | Type    | Description                                                 |
|---------------|---------|-------------------------------------------------------------|
| `offset`      | integer | Pagination offset. <i class="label label-info">optional</i> |

> HTTP request

```http
GET /api/v1/invoices/unbooked.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
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

## Sales orders ##

Get modified orders within date interval (max 31 days)

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v2/salesdata/orders.json?modified_start=:modified_start&modified_end=:modified_end</h6>
	</div>
</div>
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v2/salesdata/orders.json?modified_start=:modified_start&modified_end=:modified_end&offset=:offset&store_id=:store_id</h6>
	</div>
</div>

| GET parameter     | Type       | Description                                                       |
|-------------------|------------|-------------------------------------------------------------------|
| `store_id`        | `?integer` | optional store-id                                                 |
| `offset`          | `?integer` | optional offset, see pagination in result                         |
| `modified_start`  | `date`     | end date e.g. 2020-01-01                                          |
| `modified_end`    | `date`     | end date e.g. 2020-01-01                                          |
| `include_deleted` | `?boolean` | If `1` deleted sales orders are included with status_id=CANCELLED |

| Property                                  | Type       | Description                                                                |
|-------------------------------------------|------------|----------------------------------------------------------------------------|
| `data[].account_id`                       | `integer`  | CS Account e.g. `1`                                                        |
| `data[].store_id`                         | `integer`  | Store id e.g. `1`                                                          |
| `data[].sales_order_id`                   | `integer`  | Sales order number e.g. `50032`                                            |
| `data[].customer_id`                      | `integer`  | Customer number `6776`                                                     |
| `data[].order_type_id`                    | `integer`  | Order type id e.g. `6` (see common enum for list)                          |
| `data[].order_type_text`                  | `string`   | Order type name e.g. `Reparatie`                                           |
| `data[].order_reference_id`               | `string`   | Sales order reference id e.g. `212`                                        |
| `data[].order_reference_text`             | `string`   | Sales order reference id text e.g. `TXT212`                                |
| `data[].datetime_created`                 | `datetime` | Created at `2019-05-22 13:45:37`                                           |
| `data[].datetime_modified`                | `datetime` | Modified at `2022-04-07 15:03:32`                                          |
| `data[].datetime_preferred_delivery`      | `?date`    | Preferred delivery date                                                    |
| `data[].sales_employee_id`                | `?integer` | Sales employee ID `9`                                                      |
| `data[].last_update_employee_id`          | `?integer` | Last updated by employee ID  e.g. `9`                                      |
| `data[].status_id`                        | `integer`  | Sales order status id e.g. `9` (see common enum for list)                  |
| `data[].status_text`                      | `string`   | Sales order status text e.g. `Afgerond` (see common enum for list)         |
| `data[].cancellation_type_id`             | `integer`  | Cancellation type id e.g. `0` (see common enum for list)                   |
| `data[].cancellation_description`         | `?string`  | Cancellation description (see common enum for list)                        |
| `data[].has_invoice`                      | `boolean`  | If invoiced `true`                                                         |
| `data[].invoice_number`                   | `?integer` | Invoice number `20173328`                                                  |
| `data[].delivery_method_id`               | `integer`  | Delivery method id `0` (see common enum for list)                          |
| `data[].delivery_method_description`      | `string`   | Delivery method description `Afhalen in winkel` (see common enum for list) |
| `data[].order_item_id`                    | `integer`  | Item id within sales order `0`                                             |
| `data[].order_item_status`                | `string`   | Order item status description `Geen status`  (see common enum for list)    |
| `data[].assigned_to_customer_id`          | `integer`  | Sales order could be assigned to a different customer (lease) `6776`       |
| `data[].item_type`                        | `string`   | Description of item type `Artikelregel` (see common enum for list)         |
| `data[].barcode`                          | `string`   | Barcode of article `8237238723823`                                         |
| `data[].object_id`                        | `integer`  | ID of linked stock object `0`                                              |
| `data[].pos_group_id`                     | `integer`  | POS group id `0`  (see common enum for list)                               |
| `data[].quantity`                         | `integer`  | Quantity `1`                                                               |
| `data[].description`                      | `string`   | Description of article `Tire`                                              |
| `data[].gross_unit_price_in_vat_in_cents` | `integer`  | Gross unit price in cents `9900`                                           |
| `data[].unit_discount_in_vat_in_cents`    | `integer`  | Unit discount amount in cents  `1000`                                      |
| `data[].nett_line_price_in_vat_in_cents`  | `integer`  | Nett line price in cents `8900`                                            |
| `data[].vat_amount_cents`                 | `integer`  | VAT amount in cents e.g. `1546`                                            |
| `data[].vat_percentage`                   | `decimal`  | VAT percentage `21`                                                        |
| `pagination.count`                        | `integer`  | Number of items `3`                                                        |
| `pagination.next_offset`                  | `?integer` | If specified call the api again with offset parameter                      |

> HTTP request

```http
GET /api/v2/salesdata/orders.json?modified_start=2022-04-01&modified_end=2022-04-15 HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 1655

{
    "data": [
        {
            "account_id": 1,
            "store_id": 1,
            "sales_order_id": 54230,
            "customer_id": 235270570,
            "order_type_id": 6,
            "order_type_text": "Reparatie",
            "order_reference_id": "",
            "order_reference_text": "",
            "datetime_created": "2022-04-13 17:04:00",
            "datetime_modified": "2022-04-13 17:04:00",
            "datetime_preferred_delivery": null,
            "sales_employee_id": 2001,
            "last_update_employee_id": 2001,
            "status_id": 2,
            "status_text": "In behandeling",
            "cancellation_type_id": 0,
            "cancellation_description": null,
            "has_invoice": false,
            "invoice_number": 0,
            "delivery_method_id": 0,
            "delivery_method_description": "Afhalen in winkel",
            "order_item_id": 0,
            "order_item_status": "Geen status",
            "assigned_to_customer_id": 235270570,
            "item_type": "Artikelregel",
            "barcode": "",
            "object_id": 0,
            "pos_group_id": 0,
            "quantity": 0,
            "description": "-",
            "gross_unit_price_in_vat_in_cents": 0,
            "unit_discount_in_vat_in_cents": 0,
            "nett_line_price_in_vat_in_cents": 0,
            "vat_amount_cents": 0,
            "vat_percentage": 0
        },
        {
            "account_id": 1,
            "store_id": 1,
            "sales_order_id": 54228,
            "customer_id": 235269158,
            "order_type_id": 6,
            "order_type_text": "Reparatie",
            "order_reference_id": "",
            "order_reference_text": "",
            "datetime_created": "2022-04-13 17:03:15",
            "datetime_modified": "2022-04-13 17:03:15",
            "datetime_preferred_delivery": null,
            "sales_employee_id": 2001,
            "last_update_employee_id": 2001,
            "status_id": 2,
            "status_text": "In behandeling",
            "cancellation_type_id": 0,
            "cancellation_description": null,
            "has_invoice": false,
            "invoice_number": 0,
            "delivery_method_id": 0,
            "delivery_method_description": "Afhalen in winkel",
            "order_item_id": 1,
            "order_item_status": "Geen status",
            "assigned_to_customer_id": 235269158,
            "item_type": "Arbeid",
            "barcode": "",
            "object_id": 0,
            "pos_group_id": 2,
            "quantity": 1,
            "description": "Reparatie laag BTW-tarief",
            "gross_unit_price_in_vat_in_cents": 3792,
            "unit_discount_in_vat_in_cents": 0,
            "nett_line_price_in_vat_in_cents": 3792,
            "vat_amount_cents": 313,
            "vat_percentage": 9
        },
        {
            "account_id": 1,
            "store_id": 1,
            "sales_order_id": 54228,
            "customer_id": 235269158,
            "order_type_id": 6,
            "order_type_text": "Reparatie",
            "order_reference_id": "",
            "order_reference_text": "",
            "datetime_created": "2022-04-13 17:03:15",
            "datetime_modified": "2022-04-13 17:03:15",
            "datetime_preferred_delivery": null,
            "sales_employee_id": 2001,
            "last_update_employee_id": 2001,
            "status_id": 2,
            "status_text": "In behandeling",
            "cancellation_type_id": 0,
            "cancellation_description": null,
            "has_invoice": false,
            "invoice_number": 0,
            "delivery_method_id": 0,
            "delivery_method_description": "Afhalen in winkel",
            "order_item_id": 2,
            "order_item_status": "Geen status",
            "assigned_to_customer_id": 235269158,
            "item_type": "Artikelregel",
            "barcode": "4026495099707",
            "object_id": 0,
            "pos_group_id": 5,
            "quantity": 1,
            "description": "Schwalbe binnenband 28X1.1/2 SV19",
            "gross_unit_price_in_vat_in_cents": 850,
            "unit_discount_in_vat_in_cents": 0,
            "nett_line_price_in_vat_in_cents": 850,
            "vat_amount_cents": 148,
            "vat_percentage": 21
        }
    ],
    "pagination": {
        "count": 3,
        "next_offset": null
    }
}
```

## Payments ##

Get payments within date interval (max 31 days)

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/salesdata/payments.json?start_date=:start_date&end_date=:end_date</h6>
	</div>
</div>

| GET parameter | Type   | Description                |
|---------------|--------|----------------------------|
| `start_date`  | `date` | start date e.g. 2020-01-01 |
| `end_date`    | `date` | end date e.g. 2020-01-01   |

| Property                      | Type       | Description                                                                                                                           |
|-------------------------------|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| `customer_id`                 | `?integer` | Customer id `332107`                                                                                                                  |
| `invoice_number`              | `?integer` | Invoice number `365259` (may be null for advance payments)                                                                            |
| `related_to_invoice_number`   | `?integer` | Related to another parent invoice number                                                                                              |
| `sales_order_id`              | `?integer` | Sales order id `476953`                                                                                                               |
| `ecommerce_reference_text`    | `?string`  | Sales order reference text `reference_129223`                                                                                         |
| `ecommerce_reference_id`      | `?string`  | Sales order reference id `129223`                                                                                                     |
| `payments`                    | `object[]` | List of payments                                                                                                                      |
| `payments[].payment_id`       | `integer`  | ID of payment `65444361`                                                                                                              |
| `payments[].store_id`         | `integer`  | Store id `1`                                                                                                                          |
| `payments[].book_location_id` | `integer`  | Book location id in POS `1`                                                                                                           |
| `payments[].method`           | `string`   | Payment method description `Contant` `Creditcard` `Chip` `Tegoedbon(nen)` `Spaarpunten` `Retour` `Bank` `PSP` `Rembours` `Ecocheques` |
| `payments[].method_id`        | `integer`  | Payment method id `1` (see common enum for list)                                                                                      |
| `payments[].amount_cents`     | `integer`  | Amount of payment in cents `6999`                                                                                                     |
| `payments[].book_date`        | `string`   | Date booked `01-04-2022 15:31:44`                                                                                                     |
| `payments[].created_at`       | `string`   | Date created `01-04-2022 15:31:44`                                                                                                    |
| `psp`                         | `object[]` | Array of payment service provider information (e.g. PAY.)                                                                             |
| `psp[].psp_reference`         | `string`   | PSP reference `17232323571X84a7d`                                                                                                     |
| `psp[].psp_reference_2`       | `string`   | PSP reference 2 `fb9c911850f4edfe214ff3cdfb214dbef9e8e599`                                                                            |
| `psp[].amount_cents`          | `integer`  | Amount of PSP payment `6999`                                                                                                          |

> HTTP request

```http
GET /api/v1/salesdata/payments.json?start_date=2022-04-01&end_date=2022-04-15 HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 1655

[
  {
    "customer_id": null,
    "invoice_number": 365075,
    "related_to_invoice_number": null,
    "sales_order_id": null,
    "ecommerce_reference_text": null,
    "ecommerce_reference_id": null,
    "payments": [
      {
        "payment_id": 65423367,
        "store_id": 7,
        "book_location_id": 1,
        "method": "Pin",
        "method_id": 1,
        "amount_cents": 850,
        "book_date": "01-04-2022 10:09:26",
        "created_at": "01-04-2022 10:09:27"
      }
    ],
    "psp": [
      {
        "psp_reference": "1726172361X338a1",
        "psp_reference_2": "4b94747349c0afa0e0f6ec58dcbe717e1b32d7b0",
        "amount_cents": 850
      }
    ]
  },
  {
    "customer_id": 332107,
    "invoice_number": 365259,
    "related_to_invoice_number": null,
    "sales_order_id": 476953,
    "ecommerce_reference_text": "reference_129223",
    "ecommerce_reference_id": "129223",
    "payments": [
      {
        "payment_id": 65423591,
        "store_id": 1,
        "book_location_id": 1,
        "method": "Bank",
        "method_id": 11,
        "amount_cents": 228900,
        "book_date": "01-04-2022 10:14:18",
        "created_at": "01-04-2022 10:14:18"
      },
      {
        "payment_id": 65444361,
        "store_id": 1,
        "book_location_id": 1,
        "method": "Pin",
        "method_id": 1,
        "amount_cents": 6999,
        "book_date": "01-04-2022 15:31:44",
        "created_at": "01-04-2022 15:31:44"
      }
    ],
    "psp": [
      {
        "psp_reference": "17232323571X84a7d",
        "psp_reference_2": "fb9c911850f4edfe214ff3cdfb214dbef9e8e599",
        "amount_cents": 6999
      }
    ]
  }
]
```

## Insurances ##

Get insurances for objects created within date interval (max 31 days). The information may not be up-to-date with the
information known at the insurance company. This information is based on created insurance applications.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/stock-objects/insurance/list.json?start_date=:start_date&end_date=:end_date</h6>
	</div>
</div>

| GET parameter | Type   | Description                |
|---------------|--------|----------------------------|
| `start_date`  | `date` | start date e.g. 2020-01-01 |
| `end_date`    | `date` | end date e.g. 2020-01-01   |

| Property                  | Type      | Description                                                                |
|---------------------------|-----------|----------------------------------------------------------------------------|
| `insurance_id`            | `integer` | ID of insurance application `1182027`                                      |
| `customer_id`             | `integer` | Customer ID e.g. `334357`                                                  |
| `created_at`              | `date`    | Date created e.g. `15-04-2022`                                             |
| `stock_object_id`         | `integer` | Stock object ID `786080`                                                   |
| `insurance_company`       | `string`  | Name of insurance company `KING`                                           |
| `reference_id`            | `integer` | Reference ID `0`                                                           |
| `policy_number`           | `integer` | Policy Number (if available) `12212`                                       |
| `insurance_starting_date` | `date`    | Start date of the insurance `15-04-2022`                                   |
| `description`             | `string`  | Name of the insurance e.g. `E-bike Casco Compleet - 3 jaar - Aut. Incasso` |
| `policy_costs`            | `integer` | Costs of the policy in cents `650`                                         |
| `insured_amount`          | `integer` | Insured amount in cents `299900`                                           |
| `premium_amount`          | `integer` | Insurance premium in cents `19895`                                         |

> HTTP request

```http
GET /api/v1/stock-objects/insurance/list.json??start_date=2022-04-01&end_date=2022-04-15 HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 903

[
    {
        "insurance_id": 1168101,
        "customer_id": 317247,
        "created_at": "01-04-2022",
        "stock_object_id": 775832,
        "insurance_company": "UNIGARANT",
        "reference_id": 0,
        "policy_number": 143123238,
        "insurance_starting_date": "01-04-2022",
        "description": "Onbekend",
        "policy_costs": 968,
        "insured_amount": 6300,
        "premium_amount": 5371
    },
    {
        "insurance_id": 1168175,
        "customer_id": 332105,
        "created_at": "01-04-2022",
        "stock_object_id": 781192,
        "insurance_company": "KING",
        "reference_id": 0,
        "policy_number": 0,
        "insurance_starting_date": "01-04-2022",
        "description": "E-bike casco compleet jaarpremie Aut. Incasso",
        "policy_costs": 650,
        "insured_amount": 176900,
        "premium_amount": 7343
    }
]
```
