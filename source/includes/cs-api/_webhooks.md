# Webhooks #

Receive updates from CycleSoftware for specific entities.

### Webhook request

The payload is a raw POST of a JSON string to your server. Several headers are included:

| Header                      | Description                                                     |
|-----------------------------|-----------------------------------------------------------------|
| `X-CycleSoftware-Delivery`  | Unique UUID of the webhook message. Same value JSON id property |
| `X-CycleSoftware-Event`     | Event name. Same value as JSON event_name property              |
| `X-CycleSoftware-Signature` | HMAC of the payload using your hash secret                      |

### Payload structure

Every JSON payload has the same structure. The payload object is different per event.

| Property          | Type      | Description                                                |
|-------------------|-----------|------------------------------------------------------------|
| `id`              | `uuid`    | Unique webhook UUID `20c5d026-68b3-11ec-90d6-0242ac120003` |
| `account_id`      | `integer` | Account ID CycleSoftware `1`                               |
| `event_name`      | `string`  | The event-name e.g. `sales_order.created`                  |
| `event_timestamp` | `float`   | Timestamp when the message was created. `1640787926.323`   |
| `payload`         | `object`  | The actual payload of the event                            |

> Payload structure

```json
{
  "id": "20c5d026-68b3-11ec-90d6-0242ac120003",
  "account_id": 1,
  "event_name": "event.sub_name",
  "event_timestamp": 1640787926.323,
  "payload": {}
}
```

## Customers ##

| Event name         | Description                        |
|--------------------|------------------------------------|
| `customer.created` | Fired when the customer is created |
| `customer.updated` | Fired when the customer is updated |

### Properties

| Property                                   | Type       | Description                                                           |
|--------------------------------------------|------------|:----------------------------------------------------------------------|
| `customer.customer_barcode`                | `string`   | (deprecated) Reference of the customer e.g. `REF1212`                 |
| `customer.prefix`                          | `string`   | (deprecated) Name prefix e.g. `Dhr./Mevr. `                           |
| `customer.country`                         | `string`   | (deprecated) Country (deprecated) see country_code_iso_3166 e.g. `NL` |
| `customer.name_prefix`                     | `?string`  | (deprecated)                                                          |
| `customer.iban`                            | `string`   | IBAN bank account                                                     |
| `customer.customer_id`                     | `integer`  | Customer ID e.g. `6667`                                               |
| `customer.customer_type_name`              | `string`   | Customer type see common enum e.g. `Klant`                            |
| `customer.customer_reference`              | `string`   | Customer reference e.g. `REF1212`                                     |
| `customer.postcode`                        | `string`   | Postal code e.g. `1000AA`                                             |
| `customer.house_number`                    | `string`   | Housenumber e.g. `2522`                                               |
| `customer.house_number_postfix`            | `string`   | Housenumber postfix e.g. `B`                                          |
| `customer.attn`                            | `string`   | Attention of e.g. `Name of person`                                    |
| `customer.title`                           | `string`   | Title of customer e.g. `Dhr./Mevr. `                                  |
| `customer.first_name`                      | `string`   | Initials e.g. `Adri`                                                  |
| `customer.initials`                        | `string`   | Initials e.g. `C.G.`                                                  |
| `customer.insertion`                       | `string`   | Name insertion e.g. `van`                                             |
| `customer.name`                            | `string`   | (Sur)name e.g. `Wijk`                                                 |
| `customer.street`                          | `string`   | Street name e.g. `Aalsburg`                                           |
| `customer.city`                            | `string`   | City name e.g. `Amsterdam`                                            |
| `customer.country_code_iso_3166`           | `string`   | Country code e.g. `NL`                                                |
| `customer.email`                           | `string`   | Customer E-mail e.g. `test@test.nl`                                   |
| `customer.discount_percentage`             | `integer`  | Default discount percentage e.g. `0`                                  |
| `customer.datetime_created`                | `?string`  | datetime created if known (null if unknown)                           |
| `customer.phone_numbers`                   | `object[]` | array of phone numbers                                                |
| `customer.phone_numbers[].phone_number_id` | `string`   | ID `mob`, `tel` or stringed ID e.g. `10589`                           |
| `customer.phone_numbers[].customer_id`     | `integer`  | Customer ID `6667`                                                    |
| `customer.phone_numbers[].phone_number`    | `string`   | Phone number `06-12345678`                                            |
| `customer.phone_numbers[].name`            | `string`   | Name associated with the phone number e.g. `Sjaak`                    |

> Payload structure

```json
{
  "id": "5e2435ef-bd25-4399-9332-2a8d3c9e5830",
  "account_id": 1,
  "event_name": "customer.updated",
  "event_timestamp": 1677599374.04,
  "payload": {
    "customer": {
      "customer_id": 20,
      "customer_type_name": "Lease-rijder",
      "customer_reference": "600008000011700",
      "postcode": "9999AA",
      "house_number": "132",
      "house_number_postfix": "a",
      "attn": "",
      "title": "Dhr.",
      "initials": "P",
      "insertion": "van",
      "first_name": "Peter",
      "name": "Wijk",
      "street": "Hoogheem",
      "city": "Boxtel",
      "country_code_iso_3166": "AF",
      "email": "email20@example.nl",
      "discount_percentage": 0,
      "datetime_created": "2023-02-12 12:30:44",
      "phone_numbers": [
        {
          "phone_number_id": "mob",
          "customer_id": 20,
          "phone_number": "",
          "name": "Peter van Wijk"
        },
        {
          "phone_number_id": "tel",
          "customer_id": 20,
          "phone_number": "09-10000020",
          "name": "Peter van Wijk"
        },
        {
          "phone_number_id": "75189",
          "customer_id": 20,
          "phone_number": "09-10075189",
          "name": "Peter van Wijk alternatief"
        }
      ],
      "customer_barcode": "600008000011700",
      "prefix": "Dhr.",
      "country": "AF",
      "name_prefix": null,
      "iban": "NL00BANK1000000020",
      "date_of_birth": "1992-11-22"
    }
  }
}
```

## Sales orders ##

| Event name             | Description                                                        |
|------------------------|--------------------------------------------------------------------|
| `sales_order.created`  | Fired when the sales order is created                              |
| `sales_order.updated`  | Fired when the sales order is updated                              |
| `sales_order.deleted`  | Fired when the sales order is marked as deleted                    |
| `sales_order.invoiced` | Fired when the sales order is invoiced (sales transaction created) |

### Properties

| Property                                          | Type        | Description                                                                                |
|---------------------------------------------------|-------------|--------------------------------------------------------------------------------------------|
| `sales_order_id`                                  | `integer`   | Sales Order ID e.g. `1442`                                                                 |
| `store_id`                                        | `integer`   | Store ID within account e.g. `1`                                                           |
| `sales_employee_id`                               | `integer`   | Employee ID see common employees e.g. `1619`                                               |
| `customer_id`                                     | `integer`   | Customer ID e.g. `6667`                                                                    |
| `order_type_id`                                   | `integer`   | Order type ID, see common enum e.g. `3`                                                    |
| `order_type_text`                                 | `string`    | Order type text, see common enum  `Order`                                                  |
| `order_reference_id`                              | `string`    | Order reference ID `12212`                                                                 |
| `order_reference_text`                            | `string`    | Order reference text `REF12212`                                                            |
| `datetime_created`                                | `datetime`  | Created at e.g. `2013-09-05 12:00:00`                                                      |
| `datetime_modified`                               | `datetime`  | Modified at e.g. `2022-04-20 12:29:23`                                                     |
| `datetime_preferred_delivery`                     | `?date`     | Date of preferred delivery e.g. `2022-04-20` or `null`                                     |
| `datetime_preferred_pickup`                       | `?date`     | Date of preferred pickup e.g. `2022-04-20` or `null`                                       |
| `status_id`                                       | `integer`   | Sales order status id see common enum e.g. `2`                                             |
| `status_text`                                     | `string`    | Sales order status text see common enum e.g.  `In behandeling`                             |
| `cancellation_type_id`                            | `integer`   | Cancellation type id see common enum e.g. `0`                                              |
| `cancellation_description`                        | `?string`   | Cancellation type description see common enum                                              |
| `remarks`                                         | `string`    | Order remarks `Omschrijving 1`                                                             |
| `has_invoice`                                     | `boolean`   | True if invoice is associcated with order e.g. `false`                                     |
| `invoice_number`                                  | `integer`   | Invoice number if present `0`                                                              |
| `ship_to_customer`                                | `boolean`   | True if should ship to customer `false` (deprecated)                                       |
| `delivery_method_id`                              | `integer`   | Delivery method ID see common enum e.g. `0`                                                |
| `delivery_method_description`                     | `string`    | Delivery method description see common enum e.g. `Afhalen in winkel`                       |
| `shipment_method_description`                     | `string`    | Free description of shipment e.g. `VERZENDEN`                                              |
| `payment_method_description`                      | `string`    | Free description of shipment e.g. `IDEAL`                                                  |
| `order_items`                                     | `object[]`  | List of order items                                                                        |
| `order_items[].item_id`                           | `integer`   | ID of item within the order e.g. `2`                                                       |
| `order_items[].item_type_id`                      | `integer`   | Item type ID see common enum e.g. `1`                                                      |
| `order_items[].special_type_id`                   | `integer`   | ID if associated object if present e.g. `0`                                                |
| `order_items[].quantity`                          | `integer`   | Quantity e.g. `1`                                                                          |
| `order_items[].barcode`                           | `string`    | Barcode of item e.g. `4008496261628`                                                       |
| `order_items[].pos_group_id`                      | `integer`   | POS group see common enum e.g. `11`                                                        |
| `order_items[].description`                       | `string`    | Description of item e.g. `VARTA BATTERIE 12V38MAH V23GA`                                   |
| `order_items[].unit_price_in_vat_cents`           | `integer`   | Gross unit price in cents `225`                                                            |
| `order_items[].unit_discount_amount_in_vat_cents` | `integer`   | Unit discount in cents e.g. `0`                                                            |
| `order_items[].price_in_vat_cents`                | `integer`   | Line price in cents e.g. `225`                                                             |
| `order_items[].discount_percentage`               | `integer`   | Discount percentage e.g. `0`                                                               |
| `order_items[].vat_code`                          | `integer`   | VAT code see common enum e.g. `2`                                                          |
| `order_items[].vat_percentage`                    | `integer`   | VAT percentage e.g. `21`                                                                   |
| `order_items[].vat_amount_cents`                  | `integer`   | VAT amount in cents e.g. `39`                                                              |
| `order_items[].item_status_id`                    | `integer`   | Item status ID see common enum e.g. `0`                                                    |
| `order_items[].item_status_text`                  | `string`    | Item status text see common enum e.g. `Geen status`                                        |
| `order_items[].unit_work_time_minutes`            | `integer`   | Work time for item in minutes e.g. `0`                                                     |
| `cancelled_order_items`                           | `?object[]` | List of cancelled / non-deleted order items (same structure as `order_items`               |
| `deleted_order_items`                             | `?object[]` | List of deleted order items (same structure as `order_items`, only present once in webhook |
| `customer`                                        | `object`    | See customers webhook definition                                                           |
| `delivery_address`                                | `?object`   | Delivery address if specified, `null` if not specified                                     |
| `delivery_address.delivery_address_id`            | `integer`   | Delivery address ID e.g. `91953`                                                           |
| `delivery_address.customer_id`                    | `integer`   | Customer ID e.g. `6667`                                                                    |
| `delivery_address.is_business`                    | `boolean`   | If business address `true`                                                                 |
| `delivery_address.company_name`                   | `string`    | Company name if specified                                                                  |
| `delivery_address.name`                           | `string`    | Name of customer `Name 91953`                                                              |
| `delivery_address.street`                         | `string`    | Street name e.g. `Slangenburg`                                                             |
| `delivery_address.housenumber`                    | `string`    | House number e.g. `314`                                                                    |
| `delivery_address.housenumber_postfix`            | `string`    | House number postfix `B`                                                                   |
| `delivery_address.postcode`                       | `string`    | Postcode e.g. `8888ZZ`                                                                     |
| `delivery_address.city`                           | `string`    | City `Deventer`                                                                            |
| `delivery_address.country`                        | `string`    | Deprecated, filled with country code `NL`                                                  |
| `delivery_address.country_code_iso_3166`          | `string`    | ISO 3166 Country code e.g. `NL`                                                            |
| `delivery_address.phone_number`                   | `string`    | Phonenumber associated with address `06 12345678`                                          |
| `delivery_address.email`                          | `string`    | E-mail associated with address `email91953@example.nl`                                     |
| `delivery_address.remarks`                        | `string`    | Remarks for address `Some text`                                                            |
| `labels[]`                                        | `string[]`  | Label associated with the sales order e.g. `["label1"]`                                    |

> Payload structure

```json
{
  "id": "2f4de380-f2be-4143-bbdf-1174c5d47991",
  "account_id": 1,
  "event_name": "sales_order.updated",
  "event_timestamp": 1650450563.309,
  "payload": {
    "sales_order_id": 1442,
    "store_id": 1,
    "sales_employee_id": 1619,
    "customer_id": 6667,
    "order_type_id": 3,
    "order_type_text": "Order",
    "order_reference_id": "",
    "order_reference_text": "",
    "datetime_created": "2013-09-05 12:00:00",
    "datetime_modified": "2022-04-20 12:29:23",
    "datetime_preferred_delivery": null,
    "datetime_preferred_pickup": null,
    "status_id": 2,
    "status_text": "In behandeling",
    "cancellation_type_id": 0,
    "cancellation_description": null,
    "remarks": "Omschrijving 1",
    "has_invoice": false,
    "invoice_number": 0,
    "ship_to_customer": false,
    "delivery_method_id": 0,
    "delivery_method_description": "Afhalen in winkel",
    "shipment_method_description": "",
    "payment_method_description": "",
    "order_items": [
      {
        "item_id": 1,
        "item_type_id": 1,
        "special_type_id": 0,
        "quantity": 1,
        "barcode": "8715434065984",
        "pos_group_id": 11,
        "description": "BOBAG BOBIKE ROZE MOTIEF PRETTY PEONI (BLAUW)",
        "unit_price_in_vat_cents": 5995,
        "unit_discount_amount_in_vat_cents": 0,
        "price_in_vat_cents": 5995,
        "discount_percentage": 0,
        "vat_code": 2,
        "vat_percentage": 21,
        "vat_amount_cents": 1040,
        "item_status_id": 0,
        "item_status_text": "Geen status",
        "unit_work_time_minutes": 0
      },
      {
        "item_id": 2,
        "item_type_id": 1,
        "special_type_id": 0,
        "quantity": 1,
        "barcode": "4008496261628",
        "pos_group_id": 11,
        "description": "VARTA BATTERIE 12V38MAH V23GA",
        "unit_price_in_vat_cents": 225,
        "unit_discount_amount_in_vat_cents": 0,
        "price_in_vat_cents": 225,
        "discount_percentage": 0,
        "vat_code": 2,
        "vat_percentage": 21,
        "vat_amount_cents": 39,
        "item_status_id": 0,
        "item_status_text": "Geen status",
        "unit_work_time_minutes": 0
      }
    ],
    "customer": {
      "customer_barcode": "",
      "prefix": "Dhr./Mevr. ",
      "country": "",
      "name_prefix": null,
      "iban": "",
      "customer_id": 6667,
      "customer_type_name": "Klant",
      "customer_reference": "",
      "postcode": "1000AA",
      "house_number": "2522",
      "house_number_postfix": "",
      "attn": "",
      "title": "Dhr./Mevr. ",
      "first_name": "Carlo",
      "initials": "C.G.",
      "insertion": "van",
      "name": "Wijk",
      "street": "Aalsburg",
      "city": "Amsterdam",
      "country_code_iso_3166": "",
      "email": "test@test.nl",
      "discount_percentage": 0,
      "datetime_created": null,
      "phone_numbers": [
        {
          "phone_number_id": "mob",
          "customer_id": 6667,
          "phone_number": "",
          "name": "Dhr./Mevr. C.G. van Wijk"
        },
        {
          "phone_number_id": "tel",
          "customer_id": 6667,
          "phone_number": "000-1231231",
          "name": "Dhr./Mevr. C.G. van Wijk"
        },
        {
          "phone_number_id": "10589",
          "customer_id": 6667,
          "phone_number": "06-12345678",
          "name": "Sjaak"
        }
      ]
    },
    "delivery_address": {
      "delivery_address_id": 91953,
      "customer_id": 6667,
      "is_business": false,
      "company_name": "",
      "name": "Name 91953",
      "street": "Slangenburg",
      "housenumber": "314",
      "housenumber_postfix": "B",
      "postcode": "8888ZZ",
      "city": "Deventer",
      "country": "NL",
      "country_code_iso_3166": "NL",
      "phone_number": "06 12345678",
      "email": "email91953@example.nl",
      "remarks": "Some text"
    },
    "labels": [
      "label1"
    ]
  }
}
```

## Workshop orders ##

| Event name               | Description                                                 |
|--------------------------|-------------------------------------------------------------|
| `workshop_order.created` | Fired when the workshop order / repair is created           |
| `workshop_order.updated` | Fired when the workshop order / repair is updated           |
| `workshop_order.deleted` | Fired when the workshop order / repair is marked as deleted |

### Properties

| Property                      | Type       | Description                                                      |
|-------------------------------|------------|------------------------------------------------------------------|
| `workshop_order_id`           | `integer`  | Workshop order ID e.g. `50032`                                   |
| `repair_object_id`            | `integer`  | Repair object ID e.g. `22534`                                    |
| `reference_text`              | `string`   | Reference of order `RefText`                                     |
| `datetime_scheduled_start`    | `datetime` | Scheduled start `2019-06-07 14:30:00`                            |
| `datetime_scheduled_finished` | `datetime` | Scheduled finished `2019-06-07 16:10:00`                         |
| `mechanic_employee_id`        | `integer`  | Assigned to mechanic see common employees `40899`                |
| `repair_description`          | `string`   | Description of workshop order `Band plakken`                     |
| `status_id`                   | `integer`  | Workshop order status ID see common enum e.g. `7`                |
| `status_text`                 | `string`   | Workshop order status see common enum e.g. `Reparatie voltooid`  |
| `borrowed_object_reference`   | `string`   | Reference to borrowed object `BORROWEDBIKE1`                     |
| `total_repair_time_minutes`   | `integer`  | Total time of repair in minutes e.g. `100` (Custom time + items) |
| `custom_repair_time_minutes`  | `integer`  | Custom time of repair in minutes e.g. `0`                        |
| `sales_order`                 | `object`   | See structure of sales order webhook `                           |

> Payload example

```json
{
  "id": "34a9759f-3da7-424c-8bd8-1ce3eb22fce8",
  "account_id": 1,
  "event_name": "workshop_order.updated",
  "event_timestamp": 1649336612.447,
  "payload": {
    "workshop_order_id": 50032,
    "repair_object_id": 22534,
    "reference_text": "RefText",
    "datetime_scheduled_start": "2019-06-07 14:30:00",
    "datetime_scheduled_finished": "2019-06-07 16:10:00",
    "mechanic_employee_id": 40899,
    "repair_description": "Band plakken",
    "status_id": 7,
    "status_text": "Reparatie voltooid",
    "borrowed_object_reference": "",
    "total_repair_time_minutes": 100,
    "custom_repair_time_minutes": 0,
    "sales_order": {
      "sales_order_id": 50032,
      "store_id": 1,
      "sales_employee_id": 1001,
      "customer_id": 6776,
      "order_type_id": 6,
      "order_type_text": "Reparatie",
      "order_reference_id": "12122",
      "order_reference_text": "RefText",
      "datetime_created": "2019-05-22 13:45:37",
      "datetime_modified": "2020-08-12 15:51:57",
      "datetime_preferred_delivery": null,
      "datetime_preferred_pickup": null,
      "status_id": 9,
      "status_text": "Afgerond",
      "cancellation_type_id": 0,
      "cancellation_description": null,
      "remarks": "Opmerking",
      "has_invoice": true,
      "invoice_number": 20173328,
      "ship_to_customer": false,
      "delivery_method_id": 0,
      "delivery_method_description": "Afhalen in winkel",
      "shipment_method_description": "",
      "payment_method_description": "",
      "order_items": [],
      "customer": {
        "customer_barcode": "",
        "prefix": "",
        "country": "NL",
        "name_prefix": null,
        "iban": "",
        "customer_id": 6776,
        "customer_type_name": "Klant",
        "customer_reference": "",
        "postcode": "1000AA",
        "house_number": "1",
        "house_number_postfix": "B",
        "attn": "",
        "title": "",
        "first_name": "Jan",
        "initials": "",
        "insertion": "Van",
        "name": "Wijk",
        "street": "",
        "city": "",
        "country_code_iso_3166": "NL",
        "email": "test@cyclesoftware.nl",
        "discount_percentage": 0,
        "datetime_created": null,
        "phone_numbers": [
          {
            "phone_number_id": "mob",
            "customer_id": 6776,
            "phone_number": "0612345678",
            "name": "Van Wijk"
          },
          {
            "phone_number_id": "226441",
            "customer_id": 6776,
            "phone_number": "0612345679",
            "name": "Extra Richard"
          }
        ]
      },
      "delivery_address": null,
      "labels": [
        "label1"
      ]
    }
  }
}
```

## Sales transactions / invoices ##

| Event name                  | Description                                           |
|-----------------------------|-------------------------------------------------------|
| `sales_transaction.created` | Fired when the sales transaction / invoice is created |
| `sales_transaction.updated` | Fired when the sales transaction / invoice is updated |

### Properties

| Property                                            | Type       | Description                                                                 |
|-----------------------------------------------------|------------|-----------------------------------------------------------------------------|
| `invoice_number`                                    | `integer`  | Sales transaction number / invoice number e.g. `20210048`                   |
| `credit_invoice_number`                             | `?integer` | If this transaction is credited the credit invoice number e.g. `20210049`   |
| `debit_invoice_number`                              | `?integer` | If this transaction is a credit the original invoice number e.g. `20210047` |
| `is_final`                                          | `boolean`  | True if the transaciton is booked `false`                                   |
| `customer_id`                                       | `integer`  | Customer ID e.g. `1006` for anonymous `0`                                   |
| `store_id`                                          | `integer`  | Store ID within account `1`                                                 |
| `sales_employee_id`                                 | `integer`  | Employee ID e.g. `1001` see common employees                                |
| `sales_order_id`                                    | `?integer` | Sales Order ID                                                              |
| `workshop_order_id`                                 | `?integer` | Workshop Order ID                                                           |
| `total_amount_cents`                                | `integer`  | Total amount in cents e.g. `278820`                                         |
| `unpayed_amount_cents`                              | `integer`  | Unpayed amount in cents. `278820`                                           |
| `invoice_date`                                      | `date`     | (pro-forma) date of the invoice `2022-04-29`                                |
| `book_date`                                         | `?date`    | Book date of invoice. `null` if not booked                                  |
| `sales_items`                                       | `object[]` | Array of sales items                                                        |
| `sales_items[].sales_item_id`                       | `integer`  | Item identifier `115350527`                                                 |
| `sales_items[].item_type_id`                        | `integer`  | Item type, see common enum .e.g. `1`                                        |
| `sales_items[].special_type_id`                     | `integer`  | If associated with a stock item this is the stock item id `0`               |
| `sales_items[].quantity`                            | `integer`  | Quantity sold e.g. `1`                                                      |
| `sales_items[].barcode`                             | `string`   | Barcode of the article                                                      |
| `sales_items[].pos_group_id`                        | `integer`  | POS group id see common enum e.g. `11`                                      |
| `sales_items[].description`                         | `string`   | Line description `Diversen`                                                 |
| `sales_items[].unit_price_in_vat_cents`             | `integer`  | Gross unit price in cents `9900`                                            |
| `sales_items[].unit_discount_amount_in_vat_cents`   | `integer`  | Unit discount amount in cents `990`                                         |
| `sales_items[].price_in_vat_cents`                  | `integer`  | Line price in cents e.g. `8910`                                             |
| `sales_items[].discount_percentage`                 | `integer`  | Discount percentage `10`                                                    |
| `sales_items[].vat_code`                            | `integer`  | VAT code, see common enum `2`                                               |
| `sales_items[].vat_percentage`                      | `integer`  | VAT percentage `21`                                                         |
| `sales_items[].vat_amount_cents`                    | `integer`  | Line vat amount in cents. `1546`                                            |
| `sales_items[].identification`                      | `?object`  | Object with serial numbers if associated                                    |
| `sales_items[].identification.stock_object_id`      | `integer`  | Object associated with the item `24406`                                     |
| `sales_items[].identification.frame_number`         | `string`   | Frame number e.g. `FR0000010`                                               |
| `sales_items[].identification.key_number`           | `string`   | Key number e.g. `SL10000`                                                   |
| `sales_items[].identification.lock_number`          | `string`   | Lock number e.g. `K1212`                                                    |
| `sales_items[].identification.battery_number`       | `string`   | Battery number e.g. `B12122112`                                             |
| `sales_items[].identification.engine_number`        | `string`   | Engine number e.g. `E3322323`                                               |
| `sales_items[].identification.serial_number`        | `string`   | Serial number e.g. `S320934`                                                |
| `sales_items[].identification.license_plate_number` | `string`   | License plate number e.g. `xx-yy-zz`                                        |

> Payload example

```json
{
  "id": "f65ee643-1010-4ecb-a67e-da50dbe1ed90",
  "account_id": 1,
  "event_name": "sales_transaction.created",
  "event_timestamp": 1651242527.212,
  "payload": {
    "invoice_number": 20210047,
    "is_final": true,
    "customer_id": 0,
    "store_id": 1,
    "sales_employee_id": 1001,
    "sales_order_id": null,
    "workshop_order_id": null,
    "total_amount_cents": 200,
    "unpayed_amount_cents": 0,
    "invoice_date": "2022-04-29",
    "book_date": "2022-04-29",
    "sales_items": [
      {
        "sales_item_id": 115350525,
        "item_type_id": 1,
        "special_type_id": 0,
        "quantity": 1,
        "barcode": "",
        "pos_group_id": 8,
        "description": "Kleding",
        "unit_price_in_vat_cents": 200,
        "unit_discount_amount_in_vat_cents": 0,
        "price_in_vat_cents": 200,
        "discount_percentage": 0,
        "vat_code": 2,
        "vat_percentage": 21,
        "vat_amount_cents": 35,
        "identification": null
      }
    ]
  }
}
```

## Internal deliveries / store orders ##

| Event name            | Description                                   |
|-----------------------|-----------------------------------------------|
| `store_order.created` | Will be delivered when store order is created |
| `store_order.updated` | Will be delivered when store order is updated |

### Payload properties ###

| Property                        | Type        | Description                                                 |
|---------------------------------|-------------|-------------------------------------------------------------|
| `store_order_id`                | `integer`   | internal delivery / store order id e.g. `45287`             |
| `store_id_from`                 | `integer`   | destination store id                                        |
| `dealer_id_from`                | `integer`   | source dealer_id                                            |
| `store_id_to`                   | `integer`   | destination store_id                                        |
| `dealer_id_to`                  | `integer`   | destination dealer_id                                       |
| `store_order_type`              | `string`    | `regulier` or `via warehouse`                               |
| `store_order_type_id`           | `integer`   | 0: regular, 1: via warehouse, 2: regular via warehouse      |
| `status_id`                     | `integer`   | 0: open, 1: processed, 2: cancelled, 3: invoiced, 5: locked |
| `status`                        | `string`    | e.g. `Verwerkt`                                             |
| `remarks`                       | `string`    | e.g. `Filiaal naar filiaal levering #2341`                  |
| `processed_at`                  | `?datetime` | e.g. `2012-05-25 15:17:00`                                  |
| `related_to_sales_order_ids`    | `integer[]` | List of sales order ids related to delivery                 |
| `related_to_supplier_order_ids` | `integer[]` | List of supplier order ids related to delivery              |
| `items`                         | `object[]`  | list of items within store order                            |
| `items[].store_order_item_id`   | `integer`   | e.g. `2`                                                    |
| `items[].barcode`               | `string`    | e.g. `F.1000`                                               |
| `items[].quantity`              | `integer`   | e.g. `1`                                                    |
| `items[].item_type_id`          | `integer`   | 1: article, 2:object                                        |
| `items[].object_id`             | `?integer`  | e.g. `1000` or `null`                                       |
| `items[].description`           | `string`    | e.g. `Fiets`                                                |

> Payload

```json
{
  "id": "20c5d026-68b3-11ec-90d6-0242ac120003",
  "account_id": 1,
  "event_name": "store_order.created",
  "event_timestamp": 1640787926.323,
  "payload": {
    "store_order_id": 45287,
    "store_id_from": 1,
    "dealer_id_from": 1,
    "store_id_to": 2,
    "dealer_id_to": 131073,
    "store_order_type": "regulier",
    "store_order_type_id": 0,
    "status_id": 1,
    "status": "Verwerkt",
    "remarks": "Filiaal naar filiaal levering #2341",
    "processed_at": "2012-05-25 15:17:00",
    "related_to_sales_order_ids": [
      123223
    ],
    "related_to_supplier_order_ids": [
      2443
    ],
    "items": [
      {
        "store_order_item_id": 2,
        "barcode": "1000",
        "quantity": 1,
        "item_type_id": 1,
        "object_id": null,
        "description": "Artikel"
      },
      {
        "store_order_item_id": 2,
        "barcode": "F.1000",
        "quantity": 1,
        "item_type_id": 2,
        "object_id": 1000,
        "description": "Fiets"
      }
    ]
  }
}
```

## Payments created ##

| Event name            | Description                                                                  |
|-----------------------|------------------------------------------------------------------------------|
| `payments.created`    | Will be delivered when payments were registered for a sales order or invoice |

### Payload properties ###

| Property                         | Type       | Description                                                                            |
|----------------------------------|------------|----------------------------------------------------------------------------------------|
| `entity_type_id`                 | `integer`  | Entity type (sales transaction `5` or sales order `7`)                                 |
| `entity_id`                      | `integer`  | Sales transaction number or sales order ID e.g. `54876` (depending on `entity_type_id` |
| `payments`                       | `object[]` | array of payment objects                                                               |
| `payments[].payment_method_id`   | `integer`  | Payment method ID `2` (see common api `payment_methods`)                               |
| `payments[].payment_method_name` | `string`   | Payment method description e.g. `Contant`                                              |
| `payments[].book_date`           | `datetime` | Book date of the payment `2022-11-02 14:12:57`                                         |
| `payments[].amount_cents`        | `integer`  | Payment amount in cents `4400` for 44.00 in `payments[].currency`                      |
| `payments[].currency`            | `string`   | Payment currency e.g. `EUR`                                                            |

> Payload

```json
{
  "id": "19b4b578-79bb-4577-9b2c-c86b5fb77004",
  "account_id": 1,
  "event_name": "payments.created",
  "event_timestamp": 1667394777.764,
  "payload": {
    "entity_type_id": 7,
    "entity_id": 54876,
    "payments": [
      {
        "payment_method_id": 2,
        "payment_method_name": "Contant",
        "book_date": "2022-11-02 14:12:57",
        "amount_cents": 4400,
        "currency": "EUR"
      },
      {
        "payment_method_id": 1,
        "payment_method_name": "PIN",
        "book_date": "2022-11-02 14:12:57",
        "amount_cents": 10000,
        "currency": "EUR"
      }
    ]
  }
}
```
