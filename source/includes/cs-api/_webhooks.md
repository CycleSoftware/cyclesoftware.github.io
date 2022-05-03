#``` Webhooks #

Receive updates from CycleSoftware for specific entities.

## Internal deliveries / store orders ##

| Events                | Description                                   |
|-----------------------|-----------------------------------------------|
| `store_order.created` | Will be delivered when store order is created |

### Payload properties ###

| Property                        | Type        | Nullable | Description                                     |
|---------------------------------|-------------|----------|-------------------------------------------------|
| `store_order_id`                | `integer`   | `false`  | internal delivery / store order id e.g. `45287` |
| `store_id_from`                 | `integer`   | `false`  | destination store id                            |
| `dealer_id_from`                | `integer`   | `false`  | source dealer_id                                |
| `store_id_to`                   | `integer`   | `false`  | destination store_id                            |
| `dealer_id_to`                  | `integer`   | `false`  | destination dealer_id                           |
| `store_order_type`              | `string`    | `false`  | `regulier` or `via warehouse`                   |
| `store_order_type_id`           | `integer`   | `false`  | 0: regular, 1: via warehouse                    |
| `status_id`                     | `integer`   | `false`  | 0: open, 1: processed, 2: cancelled             |
| `status`                        | `string`    | `false`  | e.g. `Verwerkt`                                 |
| `remarks`                       | `string`    | `false`  | e.g. `Filiaal naar filiaal levering #2341`      |
| `processed_at`                  | `datetime`  | `true`   | e.g. `2012-05-25 15:17:00`                      |
| `related_to_sales_order_ids`    | `integer[]` | `false`  | List of sales order ids related to delivery     |
| `related_to_supplier_order_ids` | `integer[]` | `false`  | List of supplier order ids related to delivery  |
| `items`                         | `array`     | `false`  | list of items within store order                |
| `items[].store_order_item_id`   | `integer`   | `false`  | e.g. `2`                                        |
| `items[].barcode`               | `string`    | `false`  | e.g. `F.1000`                                   |
| `items[].quantity`              | `integer`   | `false`  | e.g. `1`                                        |
| `items[].item_type_id`          | `integer`   | `false`  | 1: article, 2:object                            |
| `items[].object_id`             | `integer`   | `true`   | e.g. `1000` or `null`                           |
| `items[].description`           | `string`    | `false`  | e.g. `Fiets`                                    |

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
