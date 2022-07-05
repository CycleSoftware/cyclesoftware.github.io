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

## Outbound orders ##

| Event name                                    | Description                                         |
|-----------------------------------------------|-----------------------------------------------------|
| `warehouse_outbound_order.created_or_updated` | Fired when the outbound order is created or updated |

### Properties

| Property                                                | Type       | Nullable | Description                                                             |
|---------------------------------------------------------|------------|----------|-------------------------------------------------------------------------|
| `payload.outbound_order_id`                             | `integer`  | `false`  | Outbound order ID e.g. `463681`                                         |
| `payload.outbound_order_type_id`                        | `integer`  | `false`  | Type of order e.g. `1`                                                  |
| `payload.outbound_order_status_id`                      | `integer`  | `false`  | Status of order e.g. `1`                                                |
| `payload.dealer_id`                                     | `integer`  | `false`  | ID of dealer e.g. `4807`                                                |
| `payload.created_at`                                    | `datetime` | `false`  | Created datetime e.g. `2022-07-05 11:07:48`                             |
| `payload.datetime_preferred_delivery`                   | `datetime` | `true`   | e.g. `2022-07-05 11:07:48` or `null`                                    |
| `payload.sales_order_id`                                | `integer`  | `true`   | Sales order ID in POS                                                   |
| `payload.order_reference_text`                          | `string`   | `false`  | String with e-commerce reference from POS                               |
| `payload.order_items`                                   | `array`    | `false`  | Array of order items                                                    |
| `payload.order_items[].outbound_order_item_id`          | `integer`  | `false`  | ID of the item e.g. `605491`                                            |
| `payload.order_items[].item_type_id`                    | `integer`  | `false`  | Item type id, see common api e.g. `2`                                   |
| `payload.order_items[].is_active`                       | `boolean`  | `false`  | if `false` the item is marked deleted                                   |
| `payload.order_items[].barcode`                         | `string`   | `false`  | Barcode of item e.g. `8713568215084`                                    |
| `payload.order_items[].quantity`                        | `integer`  | `false`  | Quantity ordered `1`                                                    |
| `payload.order_items[].quantity_claimed`                | `integer`  | `false`  | Quantity claimed stock e.g. `0`                                         |
| `payload.order_items[].quantity_shipped`                | `integer`  | `false`  | Quantity shipped e.g. `0`                                               |
| `payload.order_items[].is_blocked_for_claiming`         | `boolean`  | `false`  | `true` if blocked for claiming                                          |
| `payload.order_items[].description`                     | `string`   | `false`  | Description of item                                                     |
| `payload.order_items[].remark`                          | `string`   | `false`  | Remark of order item                                                    |
| `payload.order_items[].reference`                       | `string`   | `false`  | Reference of order item                                                 |
| `payload.order_items[].is_sold_to_customer`             | `boolean`  | `false`  | `true` if sold to customer                                              |
| `payload.order_items[].is_attached_to_outbound_item_id` | `null`     | `true`   | If not null the outbound_order_item_id of which the item is attached to |
| `payload.order_items[].is_pooled_within_stores`         | `boolean`  | `false`  | `true` if pool order                                                    |

> Payload structure

```json
{
  "id": "180c1fd6-04ab-4215-b55a-0d8710961c95",
  "account_id": 4743,
  "event_name": "warehouse_outbound_order.created_or_updated",
  "event_timestamp": 1657012068.444,
  "payload": {
    "outbound_order_id": 463681,
    "outbound_order_type_id": 1,
    "outbound_order_status_id": 1,
    "dealer_id": 4807,
    "created_at": "2022-07-05 11:07:48",
    "datetime_preferred_delivery": null,
    "sales_order_id": null,
    "order_reference_text": "",
    "order_items": [
      {
        "outbound_order_item_id": 605491,
        "item_type_id": 2,
        "is_active": true,
        "barcode": "8713568215084",
        "quantity": 1,
        "quantity_claimed": 0,
        "quantity_shipped": 0,
        "is_blocked_for_claiming": false,
        "description": "",
        "remark": "",
        "reference": "",
        "is_sold_to_customer": false,
        "is_attached_to_outbound_item_id": null,
        "is_pooled_within_stores": false
      }
    ]
  }
}
```

