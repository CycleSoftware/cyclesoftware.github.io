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

| Property                                                | Type        | Description                                                             |
|---------------------------------------------------------|-------------|-------------------------------------------------------------------------|
| `payload.outbound_order_id`                             | `integer`   | Outbound order ID e.g. `463681`                                         |
| `payload.outbound_order_type_id`                        | `integer`   | Type of order e.g. `1`                                                  |
| `payload.outbound_order_status_id`                      | `integer`   | Status of order e.g. `1`                                                |
| `payload.dealer_id`                                     | `integer`   | ID of dealer e.g. `4807`                                                |
| `payload.account_id`                                    | `integer`   | ID of account of the order e.g. `4807`                                  |
| `payload.store_id`                                      | `integer`   | ID of store of the order e.g. `1`                                       |
| `payload.created_at`                                    | `datetime`  | Created datetime e.g. `2022-07-05 11:07:48`                             |
| `payload.datetime_preferred_delivery`                   | `?datetime` | e.g. `2022-07-05 11:07:48` or `null`                                    |
| `payload.sales_order_id`                                | `?integer`  | Sales order ID in POS                                                   |
| `payload.order_reference_text`                          | `string`    | String with e-commerce reference from POS                               |
| `payload.order_items`                                   | `object[]`  | Array of order items                                                    |
| `payload.order_items[].outbound_order_item_id`          | `integer`   | ID of the item e.g. `605491`                                            |
| `payload.order_items[].item_type_id`                    | `integer`   | Item type id, see common api e.g. `2`                                   |
| `payload.order_items[].is_active`                       | `boolean`   | if `false` the item is marked deleted                                   |
| `payload.order_items[].barcode`                         | `string`    | Barcode of item e.g. `8713568215084`                                    |
| `payload.order_items[].quantity`                        | `integer`   | Quantity ordered `1`                                                    |
| `payload.order_items[].quantity_claimed`                | `integer`   | Quantity claimed stock e.g. `0`                                         |
| `payload.order_items[].quantity_shipped`                | `integer`   | Quantity shipped e.g. `0`                                               |
| `payload.order_items[].is_blocked_for_claiming`         | `boolean`   | `true` if blocked for claiming                                          |
| `payload.order_items[].description`                     | `string`    | Description of item                                                     |
| `payload.order_items[].remark`                          | `string`    | Remark of order item                                                    |
| `payload.order_items[].reference`                       | `string`    | Reference of order item                                                 |
| `payload.order_items[].is_sold_to_customer`             | `boolean`   | `true` if sold to customer                                              |
| `payload.order_items[].is_attached_to_outbound_item_id` | `?integer`  | If not null the outbound_order_item_id of which the item is attached to |
| `payload.order_items[].is_pooled_within_stores`         | `boolean`   | `true` if pool order                                                    |

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
    "account_id": 4807,
    "store_id": 1,
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


## Warehouse stock item ##

<aside class="notice">
  When a stock item is deleted no webhook will be delivered
</aside>

| Event name                                   | Description                                    |
|----------------------------------------------|------------------------------------------------|
| `warehouse_stock_item.updated`               | Fired when the stock item is updated           |
| `warehouse_stock_item.released_for_shipment` | Fired when stock item is released for shipment |

### Properties

| Property                              | Type       | Description                                                         |
|---------------------------------------|------------|---------------------------------------------------------------------|
| `warehouse_stock_item_id`             | `integer`  | Warehouse stock Item ID `285`                                       |
| `warehouse_outbound_order_id`         | `integer`  | Outbound order ID `121212` (`0` if not associated to an order)      |
| `warehouse_outbound_order_item_id`    | `integer`  | Outbound order Item ID `333233` (`0` if not associated to an order) |
| `warehouse_outbound_shipment_id`      | `integer`  | Shipment ID  `0` if not shipped                                     |
| `warehouse_outbound_shipment_item_id` | `integer`  | Shipment Item ID `0` if not shipped                                 |
| `warehouse_location.location`         | `string`   | Location in warehouse e.g. `R-1-2`                                  |
| `warehouse_location.rack_name`        | `string`   | Rack name in warehouse `R`                                          |
| `supplier_id`                         | `integer`  | Supplier ID of object e.g. `2113` (see common API suppliers)        |
| `article_id`                          | `string`   | Article number of stock item e.g. `4961`                            |
| `barcode`                             | `string`   | Barcode of stock item e.g. `2000100281620`                          |
| `battery_id`                          | `string`   | Battery ID e.g. `BAT22222`                                          |
| `customer_id`                         | `integer`  | Customer ID in POS e.g. `1006`                                      |
| `customer_order_id`                   | `integer`  | Sales order ID in POS e.g. `333`                                    |
| `employee_first_name`                 | `string`   | Employee name e.g. `First`                                          |
| `employee_last_name`                  | `string`   | Employee last name e.g. `Last`                                      |
| `frame_id`                            | `string`   | Frame ID e.g. `3232`                                                |
| `is_assembled`                        | `boolean`  | `true` if item is assembled                                         |
| `is_shipped`                          | `boolean`  | `true` if item is shipped                                           |
| `is_delivered`                        | `boolean`  | `true` if item is delivered                                         |
| `key_id`                              | `string`   | Key ID of object e.g. `2323`                                        |
| `lock_id`                             | `string`   | Lock ID of object e.g. `2323`                                       |
| `license_plate_number`                | `string`   | License plate of object e.g. `xx-yy-zz`                             |
| `order_reference_id`                  | `string`   | POS/OBO order reference ID `fvs12222`                               |
| `order_reference_text`                | `string`   | POS/OBO order reference text e.g. `REF`                             |
| `labels`                              | `string[]` | Labels associated with object e.g. `Label 1`                        |
| `sub_order_items`                     | `object[]` | Arrey of sub order items associated to item                         |
| `sub_order_items[].article_id`        | `string`   | Article ID e.g. `a3223`                                             |
| `sub_order_items[].barcode`           | `string`   | Article barcode e.g. `883273232332`                                 |
| `sub_order_items[].is_active`         | `boolean`  | `true` if order item is active                                      |
| `sub_order_items[].is_included`       | `boolean`  | `true` if item is included with item                                |
| `sub_order_items[].quantity`          | `integer`  | Quantity of sub item e.g. `3`                                       |
| `sub_order_items[].quantity_claimed`  | `integer`  | Quantity stock claimed e.g. `3`                                     |
| `sub_order_items[].reference`         | `string`   | Reference of item `ref-1`                                           |
| `sub_order_items[].remark`            | `string`   | Remark of item `remark-1`                                           |

> Payload structure

```json
{
  "id": "180c1fd6-04ab-4215-b55a-0d8710961c95",
  "account_id": 4743,
  "event_name": "warehouse_outbound_order.created_or_updated",
  "event_timestamp": 1657012068.444,
  "payload": {
    "warehouse_stock_item_id": 285,
    "warehouse_outbound_order_id": 121212,
    "warehouse_outbound_order_item_id": 333233,
    "warehouse_outbound_shipment_id": 0,
    "warehouse_outbound_shipment_item_id": 0,
    "article_id": "4961",
    "barcode": "2000100281620",
    "battery_id": "BAT22222",
    "customer_id": 1006,
    "customer_order_id": 333,
    "employee_first_name": "First",
    "employee_last_name": "Last",
    "frame_id": "3232",
    "is_assembled": true,
    "is_shipped": false,
    "is_delivered": false,
    "key_id": "2323",
    "lock_id": "2323",
    "license_plate_number": "xx-yy-zz",
    "order_reference_id": "fvs12222",
    "order_reference_text": "REF",
    "sub_order_items": [
      {
        "article_id": "a3223",
        "barcode": "883273232332",
        "is_active": true,
        "is_included": true,
        "quantity": 2,
        "quantity_claimed": 2,
        "reference": "ref-1",
        "remark": "remark-1"
      },
      {
        "article_id": "a3223",
        "barcode": "883273232332",
        "is_active": true,
        "is_included": true,
        "quantity": 3,
        "quantity_claimed": 3,
        "reference": "ref-1",
        "remark": "remark-1"
      }
    ],
    "supplier_id": 2113,
    "warehouse_location": {
      "location": "R-1-2",
      "rack_name": "R"
    },
    "labels": [
      "Label 1"
    ]
  }
}
```
