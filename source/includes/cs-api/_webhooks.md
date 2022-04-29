# Webhooks #

Receive updates from CycleSoftware for specific entities.

### Webhook request
The payload is a raw POST request to your server. Several headers are included:

| Header                      | Description                                                     |
|-----------------------------|-----------------------------------------------------------------|
| `X-CycleSoftware-Delivery`  | Unique UUID of the webhook message. Same value JSON id property |
| `X-CycleSoftware-Event`     | Event name. Same value as JSON event_name property              |
| `X-CycleSoftware-Signature` | HMAC of the payload using your hash secret                      |


### Payload structure

Every payload has the same structure. The payload object is different per entity type.

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

| Subject                | Description                                                        |
|------------------------|--------------------------------------------------------------------|
| `sales_order.created`  | Fired when the sales order is created                              |
| `sales_order.updated`  | Fired when the sales order is updated                              |
| `sales_order.deleted`  | Fired when the sales order is marked as deleted                    |
| `sales_order.invoiced` | Fired when the sales order is invoiced (sales transaction created) |

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
    "delivery_address": null,
    "labels": ["label1"]
  }
}
```


## Workshop orders ##

| Event name               | Description                                                 |
|--------------------------|-------------------------------------------------------------|
| `workshop_order.created` | Fired when the workshop order / repair is created           |
| `workshop_order.updated` | Fired when the workshop order / repair is updated           |
| `workshop_order.deleted` | Fired when the workshop order / repair is marked as deleted |

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
      "labels": ["label1"]
    }
  }
}
```

## Sales transactions / invoices ##

| Event name                  | Description                                           |
|-----------------------------|-------------------------------------------------------|
| `sales_transaction.created` | Fired when the sales transaction / invoice is created |
| `sales_transaction.updated` | Fired when the sales transaction / invoice is updated |


> Payload example

```json
{
  "id": "20c5d026-68b3-11ec-90d6-0242ac120003",
  "account_id": 1,
  "event_name": "store_order.created",
  "event_timestamp": 1640787926.323,
  "payload": {

}
```



## Internal deliveries / store orders ##

| Event name            | Description                                   |
|-----------------------|-----------------------------------------------|
| `store_order.created` | Will be delivered when store order is created |

### Payload properties ###

| Property                      | Type        | Nullable | Description                                     |
|-------------------------------|-------------|----------|-------------------------------------------------|
| store_order_id                | `integer`   | `false`  | internal delivery / store order id e.g. `45287` |
| store_id_from                 | `integer`   | `false`  | destination store id                            |
| dealer_id_from                | `integer`   | `false`  | source dealer_id                                |
| store_id_to                   | `integer`   | `false`  | destination store_id                            |
| dealer_id_to                  | `integer`   | `false`  | destination dealer_id                           |
| store_order_type              | `string`    | `false`  | `regulier` or `via warehouse`                   |
| store_order_type_id           | `integer`   | `false`  | 0: regular, 1: via warehouse                    |
| status_id                     | `integer`   | `false`  | 0: open, 1: processed, 2: cancelled             |
| status                        | `string`    | `false`  | e.g. `Verwerkt`                                 |
| remarks                       | `string`    | `false`  | e.g. `Filiaal naar filiaal levering #2341`      |
| processed_at                  | `datetime`  | `true`   | e.g. `2012-05-25 15:17:00`                      |
| related_to_sales_order_ids    | `integer[]` | `false`  | List of sales order ids related to delivery     |
| related_to_supplier_order_ids | `integer[]` | `false`  | List of supplier order ids related to delivery  |
| items                         | `array`     | `false`  | list of items within store order                |
| items[].store_order_item_id   | `integer`   | `false`  | e.g. `2`                                        |
| items[].barcode               | `string`    | `false`  | e.g. `F.1000`                                   |
| items[].quantity              | `integer`   | `false`  | e.g. `1`                                        |
| items[].item_type_id          | `integer`   | `false`  | 1: article, 2:object                            |
| items[].object_id             | `integer`   | `true`   | e.g. `1000` or `null`                           |
| items[].description           | `string`    | `false`  | e.g. `Fiets`                                    |

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
