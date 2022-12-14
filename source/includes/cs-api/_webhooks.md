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

## Sales orders ##

| Event name             | Description                                                        |
|------------------------|--------------------------------------------------------------------|
| `sales_order.created`  | Fired when the sales order is created                              |
| `sales_order.updated`  | Fired when the sales order is updated                              |
| `sales_order.deleted`  | Fired when the sales order is marked as deleted                    |
| `sales_order.invoiced` | Fired when the sales order is invoiced (sales transaction created) |

### Properties

| Property                                          | Type       | Nullable |     | Description                                                           |
|---------------------------------------------------|------------|----------|:----|-----------------------------------------------------------------------|
| `sales_order_id`                                  | `integer`  | `false`  |     | Sales Order ID e.g. `1442`                                            |
| `store_id`                                        | `integer`  | `false`  |     | Store ID within account e.g. `1`                                      |
| `sales_employee_id`                               | `integer`  | `false`  |     | Employee ID see common employees e.g. `1619`                          |
| `customer_id`                                     | `integer`  | `false`  |     | Customer ID e.g. `6667`                                               |
| `order_type_id`                                   | `integer`  | `false`  |     | Order type ID, see common enum e.g. `3`                               |
| `order_type_text`                                 | `string`   | `false`  |     | Order type text, see common enum  `Order`                             |
| `order_reference_id`                              | `string`   | `false`  |     | Order reference ID `12212`                                            |
| `order_reference_text`                            | `string`   | `false`  |     | Order reference text `REF12212`                                       |
| `datetime_created`                                | `datetime` | `false`  |     | Created at e.g. `2013-09-05 12:00:00`                                 |
| `datetime_modified`                               | `datetime` | `false`  |     | Modified at e.g. `2022-04-20 12:29:23`                                |
| `datetime_preferred_delivery`                     | `null`     | `true`   |     | Date of preferred delivery e.g. `2022-04-20` or `null`                |
| `datetime_preferred_pickup`                       | `null`     | `true`   |     | Date of preferred pickup e.g. `2022-04-20` or `null`                  |
| `status_id`                                       | `integer`  | `false`  |     | Sales order status id see common enum e.g. `2`                        |
| `status_text`                                     | `string`   | `false`  |     | Sales order status text see common enum e.g.  `In behandeling`        |
| `cancellation_type_id`                            | `integer`  | `false`  |     | Cancellation type id see common enum e.g. `0`                         |
| `cancellation_description`                        | `null`     | `true`   |     | Cancellation type description see common enum                         |
| `remarks`                                         | `string`   | `false`  |     | Order remarks `Omschrijving 1`                                        |
| `has_invoice`                                     | `boolean`  | `false`  |     | True if invoice is associcated with order e.g. `false`                |
| `invoice_number`                                  | `integer`  | `false`  |     | Invoice number if present `0`                                         |
| `ship_to_customer`                                | `boolean`  | `false`  |     | True if should ship to customer `false` (deprecated)                  |
| `delivery_method_id`                              | `integer`  | `false`  |     | Delivery method ID see common enum e.g. `0`                           |
| `delivery_method_description`                     | `string`   | `false`  |     | Delivery method description see common enum e.g. `Afhalen in winkel`  |
| `shipment_method_description`                     | `string`   | `false`  |     | Free description of shipment e.g. `VERZENDEN`                         |
| `payment_method_description`                      | `string`   | `false`  |     | Free description of shipment e.g. `IDEAL`                             |
| `order_items`                                     | `array`    | `false`  |     | List of order items                                                   |
| `order_items[].item_id`                           | `integer`  | `false`  |     | ID of item within the order e.g. `2`                                  |
| `order_items[].item_type_id`                      | `integer`  | `false`  |     | Item type ID see common enum e.g. `1`                                 |
| `order_items[].special_type_id`                   | `integer`  | `false`  |     | ID if associated object if present e.g. `0`                           |
| `order_items[].quantity`                          | `integer`  | `false`  |     | Quantity e.g. `1`                                                     |
| `order_items[].barcode`                           | `string`   | `false`  |     | Barcode of item e.g. `4008496261628`                                  |
| `order_items[].pos_group_id`                      | `integer`  | `false`  |     | POS group see common enum e.g. `11`                                   |
| `order_items[].description`                       | `string`   | `false`  |     | Description of item e.g. `VARTA BATTERIE 12V38MAH V23GA`              |
| `order_items[].unit_price_in_vat_cents`           | `integer`  | `false`  |     | Gross price in cents `225`                                            |
| `order_items[].unit_discount_amount_in_vat_cents` | `integer`  | `false`  |     | Unit discount in cents e.g. `0`                                       |
| `order_items[].price_in_vat_cents`                | `integer`  | `false`  |     | Line price in cents e.g. `225`                                        |
| `order_items[].discount_percentage`               | `integer`  | `false`  |     | Discount percentage e.g. `0`                                          |
| `order_items[].vat_code`                          | `integer`  | `false`  |     | VAT code see common enum e.g. `2`                                     |
| `order_items[].vat_percentage`                    | `integer`  | `false`  |     | VAT percentage e.g. `21`                                              |
| `order_items[].vat_amount_cents`                  | `integer`  | `false`  |     | VAT amount in cents e.g. `39`                                         |
| `order_items[].item_status_id`                    | `integer`  | `false`  |     | Item status ID see common enum e.g. `0`                               |
| `order_items[].item_status_text`                  | `string`   | `false`  |     | Item status text see common enum e.g. `Geen status`                   |
| `order_items[].unit_work_time_minutes`            | `integer`  | `false`  |     | Work time for item in minutes e.g. `0`                                |
| `customer.customer_barcode`                       | `string`   | `false`  |     | (deprecated) Reference of the customer e.g. `REF1212`                 |
| `customer.prefix`                                 | `string`   | `false`  |     | (deprecated) Name prefix e.g. `Dhr./Mevr. `                           |
| `customer.country`                                | `string`   | `false`  |     | (deprecated) Country (deprecated) see country_code_iso_3166 e.g. `NL` |
| `customer.name_prefix`                            | `string`   | `true`   |     | (deprecated)                                                          |
| `customer.iban`                                   | `string`   | `false`  |     | IBAN bank account                                                     |
| `customer.customer_id`                            | `integer`  | `false`  |     | Customer ID e.g. `6667`                                               |
| `customer.customer_type_name`                     | `string`   | `false`  |     | Customer type see common enum e.g. `Klant`                            |
| `customer.customer_reference`                     | `string`   | `false`  |     | Customer reference e.g. `REF1212`                                     |
| `customer.postcode`                               | `string`   | `false`  |     | Postal code e.g. `1000AA`                                             |
| `customer.house_number`                           | `string`   | `false`  |     | Housenumber e.g. `2522`                                               |
| `customer.house_number_postfix`                   | `string`   | `false`  |     | Housenumber postfix e.g. `B`                                          |
| `customer.attn`                                   | `string`   | `false`  |     | e.g. ``                                                               |
| `customer.title`                                  | `string`   | `false`  |     | Title of customer e.g. `Dhr./Mevr. `                                  |
| `customer.first_name`                             | `string`   | `false`  |     | Initials e.g. `Adri`                                                  |
| `customer.initials`                               | `string`   | `false`  |     | Initials e.g. `C.G.`                                                  |
| `customer.insertion`                              | `string`   | `false`  |     | Name insertion e.g. `van`                                             |
| `customer.name`                                   | `string`   | `false`  |     | (Sur)name e.g. `Wijk`                                                 |
| `customer.street`                                 | `string`   | `false`  |     | Street name e.g. `Aalsburg`                                           |
| `customer.city`                                   | `string`   | `false`  |     | City name e.g. `Amsterdam`                                            |
| `customer.country_code_iso_3166`                  | `string`   | `false`  |     | Country code e.g. `NL`                                                |
| `customer.email`                                  | `string`   | `false`  |     | Customer E-mail e.g. `test@test.nl`                                   |
| `customer.discount_percentage`                    | `integer`  | `false`  |     | Default discount percentage e.g. `0`                                  |
| `customer.datetime_created`                       | `string`   | `true`   |     | datetime created if known (null if unknown)                           |
| `customer.phone_numbers`                          | `array`    | `false`  |     | array of phone numbers                                                |
| `customer.phone_numbers[].phone_number_id`        | `string`   | `false`  |     | ID `mob`, `tel` or stringed ID e.g. `10589`                           |
| `customer.phone_numbers[].customer_id`            | `integer`  | `false`  |     | Customer ID `6667`                                                    |
| `customer.phone_numbers[].phone_number`           | `string`   | `false`  |     | Phone number `06-12345678`                                            |
| `customer.phone_numbers[].name`                   | `string`   | `false`  |     | Name associated with the phone number e.g. `Sjaak`                    |
| `delivery_address`                                | `object`   | `true`   |     | Delivery address if specified, `null` if not specified                |
| `delivery_address.delivery_address_id`            | `integer`  | `false`  |     | Delivery address ID e.g. `91953`                                      |
| `delivery_address.customer_id`                    | `integer`  | `false`  |     | Customer ID e.g. `6667`                                               |
| `delivery_address.is_business`                    | `boolean`  | `false`  |     | If business address `true`                                            |
| `delivery_address.company_name`                   | `string`   | `false`  |     | Company name if specified                                             |
| `delivery_address.name`                           | `string`   | `false`  |     | Name of customer `Name 91953`                                         |
| `delivery_address.street`                         | `string`   | `false`  |     | Street name e.g. `Slangenburg`                                        |
| `delivery_address.housenumber`                    | `string`   | `false`  |     | House number e.g. `314`                                               |
| `delivery_address.housenumber_postfix`            | `string`   | `false`  |     | House number postfix `B`                                              |
| `delivery_address.postcode`                       | `string`   | `false`  |     | Postcode e.g. `8888ZZ`                                                |
| `delivery_address.city`                           | `string`   | `false`  |     | City `Deventer`                                                       |
| `delivery_address.country`                        | `string`   | `false`  |     | Deprecated, filled with country code `NL`                             |
| `delivery_address.country_code_iso_3166`          | `string`   | `false`  |     | ISO 3166 Country code e.g. `NL`                                       |
| `delivery_address.phone_number`                   | `string`   | `false`  |     | Phonenumber associated with address `06 12345678`                     |
| `delivery_address.email`                          | `string`   | `false`  |     | E-mail associated with address `email91953@example.nl`                |
| `delivery_address.remarks`                        | `string`   | `false`  |     | Remarks for address `Some text`                                       |
| `labels`                                          | `array`    | `false`  |     | Array of label strings                                                |
| `labels[]`                                        | `string`   | `false`  |     | Label associated with the sales order e.g. `label1`                   |

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

| Property                      | Type       | Nullable | Description                                                      |
|-------------------------------|------------|----------|------------------------------------------------------------------|
| `workshop_order_id`           | `integer`  | `false`  | Workshop order ID e.g. `50032`                                   |
| `repair_object_id`            | `integer`  | `false`  | Repair object ID e.g. `22534`                                    |
| `reference_text`              | `string`   | `false`  | Reference of order `RefText`                                     |
| `datetime_scheduled_start`    | `datetime` | `false`  | Scheduled start `2019-06-07 14:30:00`                            |
| `datetime_scheduled_finished` | `datetime` | `false`  | Scheduled finished `2019-06-07 16:10:00`                         |
| `mechanic_employee_id`        | `integer`  | `false`  | Assigned to mechanic see common employees `40899`                |
| `repair_description`          | `string`   | `false`  | Description of workshop order `Band plakken`                     |
| `status_id`                   | `integer`  | `false`  | Workshop order status ID see common enum e.g. `7`                |
| `status_text`                 | `string`   | `false`  | Workshop order status see common enum e.g. `Reparatie voltooid`  |
| `borrowed_object_reference`   | `string`   | `false`  | Reference to borrowed object `BORROWEDBIKE1`                     |
| `total_repair_time_minutes`   | `integer`  | `false`  | Total time of repair in minutes e.g. `100` (Custom time + items) |
| `custom_repair_time_minutes`  | `integer`  | `false`  | Custom time of repair in minutes e.g. `0`                        |
| `sales_order`                 | `object`   | `false`  | See structure of sales order webhook `                           |

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

| Property                                            | Type      | Nullable / optional | Description                                                                 |
|-----------------------------------------------------|-----------|---------------------|-----------------------------------------------------------------------------|
| `invoice_number`                                    | `integer` | `false`             | Sales transaction number / invoice number e.g. `20210048`                   |
| `credit_invoice_number`                             | `integer` | `optional`          | If this transaction is credited the credit invoice number e.g. `20210049`   |
| `debit_invoice_number`                              | `integer` | `optional`          | If this transaction is a credit the original invoice number e.g. `20210047` |
| `is_final`                                          | `boolean` | `false`             | True if the transaciton is booked `false`                                   |
| `customer_id`                                       | `integer` | `false`             | Customer ID e.g. `1006` for anonymous `0`                                   |
| `store_id`                                          | `integer` | `false`             | Store ID within account `1`                                                 |
| `sales_employee_id`                                 | `integer` | `false`             | Employee ID e.g. `1001` see common employees                                |
| `sales_order_id`                                    | `integer` | `true`              | Sales Order ID                                                              |
| `workshop_order_id`                                 | `integer` | `true`              | Workshop Order ID                                                           |
| `total_amount_cents`                                | `integer` | `false`             | Total amount in cents e.g. `278820`                                         |
| `unpayed_amount_cents`                              | `integer` | `false`             | Unpayed amount in cents. `278820`                                           |
| `invoice_date`                                      | `date`    | `false`             | (pro-forma) date of the invoice `2022-04-29`                                |
| `book_date`                                         | `date`    | `true`              | Book date of invoice. `null` if not booked                                  |
| `sales_items`                                       | `array`   | `false`             | Array of sales items                                                        |
| `sales_items[].sales_item_id`                       | `integer` | `false`             | Item identifier `115350527`                                                 |
| `sales_items[].item_type_id`                        | `integer` | `false`             | Item type, see common enum .e.g. `1`                                        |
| `sales_items[].special_type_id`                     | `integer` | `false`             | If associated with a stock item this is the stock item id `0`               |
| `sales_items[].quantity`                            | `integer` | `false`             | Quantity sold e.g. `1`                                                      |
| `sales_items[].barcode`                             | `string`  | `false`             | Barcode of the article                                                      |
| `sales_items[].pos_group_id`                        | `integer` | `false`             | POS group id see common enum e.g. `11`                                      |
| `sales_items[].description`                         | `string`  | `false`             | Line description `Diversen`                                                 |
| `sales_items[].unit_price_in_vat_cents`             | `integer` | `false`             | Gross unit price in cents `9900`                                            |
| `sales_items[].unit_discount_amount_in_vat_cents`   | `integer` | `false`             | Unit discount amount in cents `990`                                         |
| `sales_items[].price_in_vat_cents`                  | `integer` | `false`             | Line price in cents e.g. `8910`                                             |
| `sales_items[].discount_percentage`                 | `integer` | `false`             | Discount percentage `10`                                                    |
| `sales_items[].vat_code`                            | `integer` | `false`             | VAT code, see common enum `2`                                               |
| `sales_items[].vat_percentage`                      | `integer` | `false`             | VAT percentage `21`                                                         |
| `sales_items[].vat_amount_cents`                    | `integer` | `false`             | Line vat amount in cents. `1546`                                            |
| `sales_items[].identification`                      | `object`  | `true`              | Object with serial numbers if associated                                    |
| `sales_items[].identification.stock_object_id`      | `integer` | `false`             | Object associated with the item `24406`                                     |
| `sales_items[].identification.frame_number`         | `string`  | `false`             | Frame number e.g. `FR0000010`                                               |
| `sales_items[].identification.key_number`           | `string`  | `false`             | Key number e.g. `SL10000`                                                   |
| `sales_items[].identification.lock_number`          | `string`  | `false`             | Lock number e.g. `K1212`                                                    |
| `sales_items[].identification.battery_number`       | `string`  | `false`             | Battery number e.g. `B12122112`                                             |
| `sales_items[].identification.engine_number`        | `string`  | `false`             | Engine number e.g. `E3322323`                                               |
| `sales_items[].identification.serial_number`        | `string`  | `false`             | Serial number e.g. `S320934`                                                |
| `sales_items[].identification.license_plate_number` | `string`  | `false`             | License plate number e.g. `xx-yy-zz`                                        |

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

| Property                        | Type        | Nullable | Description                                                 |
|---------------------------------|-------------|----------|-------------------------------------------------------------|
| `store_order_id`                | `integer`   | `false`  | internal delivery / store order id e.g. `45287`             |
| `store_id_from`                 | `integer`   | `false`  | destination store id                                        |
| `dealer_id_from`                | `integer`   | `false`  | source dealer_id                                            |
| `store_id_to`                   | `integer`   | `false`  | destination store_id                                        |
| `dealer_id_to`                  | `integer`   | `false`  | destination dealer_id                                       |
| `store_order_type`              | `string`    | `false`  | `regulier` or `via warehouse`                               |
| `store_order_type_id`           | `integer`   | `false`  | 0: regular, 1: via warehouse, 2: regular via warehouse      |
| `status_id`                     | `integer`   | `false`  | 0: open, 1: processed, 2: cancelled, 3: invoiced, 5: locked |
| `status`                        | `string`    | `false`  | e.g. `Verwerkt`                                             |
| `remarks`                       | `string`    | `false`  | e.g. `Filiaal naar filiaal levering #2341`                  |
| `processed_at`                  | `datetime`  | `true`   | e.g. `2012-05-25 15:17:00`                                  |
| `related_to_sales_order_ids`    | `integer[]` | `false`  | List of sales order ids related to delivery                 |
| `related_to_supplier_order_ids` | `integer[]` | `false`  | List of supplier order ids related to delivery              |
| `items`                         | `array`     | `false`  | list of items within store order                            |
| `items[].store_order_item_id`   | `integer`   | `false`  | e.g. `2`                                                    |
| `items[].barcode`               | `string`    | `false`  | e.g. `F.1000`                                               |
| `items[].quantity`              | `integer`   | `false`  | e.g. `1`                                                    |
| `items[].item_type_id`          | `integer`   | `false`  | 1: article, 2:object                                        |
| `items[].object_id`             | `integer`   | `true`   | e.g. `1000` or `null`                                       |
| `items[].description`           | `string`    | `false`  | e.g. `Fiets`                                                |

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

| Property                         | Type       | Nullable | Description                                                                            |
|----------------------------------|------------|----------|----------------------------------------------------------------------------------------|
| `entity_type_id`                 | `integer`  | `false`  | Entity type (sales transaction `5` or sales order `7`)                                 |
| `entity_id`                      | `integer`  | `false`  | Sales transaction number or sales order ID e.g. `54876` (depending on `entity_type_id` |
| `payments`                       | `array`    | `false`  | array of payment objects                                                               |
| `payments[].payment_method_id`   | `integer`  | `false`  | Payment method ID `2` (see common api `payment_methods`)                               |
| `payments[].payment_method_name` | `string`   | `false`  | Payment method description e.g. `Contant`                                              |
| `payments[].book_date`           | `datetime` | `false`  | Book date of the payment `2022-11-02 14:12:57`                                         |
| `payments[].amount_cents`        | `integer`  | `false`  | Payment amount in cents `4400` for 44.00 in `payments[].currency`                      |
| `payments[].currency`            | `string`   | `false`  | Payment currency e.g. `EUR`                                                            |

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
