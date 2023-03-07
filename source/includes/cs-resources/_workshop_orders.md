# Workshop orders #

Read, create or update workshop orders

***Scope(s)***

- `resources`

## Workshop order (object)

| **Property**                                      | **Type**  | **Nullable** | **Description**                                            |
|---------------------------------------------------|-----------|--------------|------------------------------------------------------------|
| `workshop_order_id`                               | `integer` | `false`      | e.g. `978070`                                              |
| `sales_order_id`                                  | `integer` | `false`      | e.g. `978070`                                              |
| `customer_id`                                     | `integer` | `false`      | e.g. `24`                                                  |
| `store_id`                                        | `integer` | `false`      | e.g. `1`                                                   |
| `repair_object_id`                                | `integer` | `false`      | e.g. `1105`                                                |
| `is_active`                                       | `boolean` | `false`      | e.g. `true`                                                |
| `reference_text`                                  | `string`  | `false`      | e.g. `work_number`                                         |
| `datetime_scheduled_start`                        | `string`  | `false`      | e.g. `2023-03-07T12:13:47+01:00`                           |
| `datetime_scheduled_finished`                     | `string`  | `false`      | e.g. `2023-03-07T12:43:47+01:00`                           |
| `datetime_created`                                | `string`  | `false`      | e.g. `2023-03-07T12:13:47+01:00`                           |
| `datetime_modified`                               | `string`  | `false`      | e.g. `2023-03-07T12:13:47+01:00`                           |
| `mechanic_employee_id`                            | `integer` | `false`      | e.g. `12`                                                  |
| `created_by_employee_id`                          | `integer` | `false`      | e.g. `1`                                                   |
| `last_update_employee_id`                         | `integer` | `false`      | e.g. `1`                                                   |
| `phone_number_id`                                 | `string`  | `false`      | e.g. `tel`                                                 |
| `repair_description`                              | `string`  | `false`      | e.g. `posted repair`                                       |
| `status_id`                                       | `integer` | `false`      | e.g. `7`                                                   |
| `status_text`                                     | `string`  | `false`      | e.g. `Reparatie voltooid`                                  |
| `invoice_number`                                  | `integer` | `false`      | e.g. `0`                                                   |
| `borrowed_object_reference`                       | `string`  | `false`      |                                                            |
| `total_repair_time_minutes`                       | `integer` | `false`      | e.g. `30`                                                  |
| `custom_repair_time_minutes`                      | `integer` | `false`      | e.g. `30`                                                  |
| `repair_codes`                                    | `null`    | `true`       |                                                            |
| `service_card_codes`                              | `null`    | `true`       |                                                            |
| `delivery_method_id`                              | `integer` | `false`      | e.g. `0`                                                   |
| `order_items`                                     | `array`   | `false`      |                                                            |
| `order_items[].item_id`                           | `integer` | `false`      | e.g. `2`                                                   |
| `order_items[].item_type_id`                      | `integer` | `false`      | e.g. `1`                                                   |
| `order_items[].special_type_id`                   | `integer` | `false`      | e.g. `0`                                                   |
| `order_items[].quantity`                          | `integer` | `false`      | e.g. `1`                                                   |
| `order_items[].barcode`                           | `string`  | `false`      | e.g. `102`                                                 |
| `order_items[].pos_group_id`                      | `integer` | `false`      | e.g. `2`                                                   |
| `order_items[].description`                       | `string`  | `false`      | e.g. `In- en uitbouwen electromotor in- en uitbouwen accu` |
| `order_items[].unit_price_in_vat_cents`           | `integer` | `false`      | e.g. `9000`                                                |
| `order_items[].unit_discount_amount_in_vat_cents` | `integer` | `false`      | e.g. `0`                                                   |
| `order_items[].price_in_vat_cents`                | `integer` | `false`      | e.g. `9000`                                                |
| `order_items[].discount_percentage`               | `integer` | `false`      | e.g. `0`                                                   |
| `order_items[].vat_code`                          | `integer` | `false`      | e.g. `1`                                                   |
| `order_items[].vat_percentage`                    | `integer` | `false`      | e.g. `9`                                                   |
| `order_items[].vat_amount_cents`                  | `integer` | `false`      | e.g. `743`                                                 |
| `order_items[].item_status_id`                    | `integer` | `false`      | e.g. `0`                                                   |
| `order_items[].item_status_text`                  | `string`  | `false`      | e.g. `Geen status`                                         |
| `order_items[].unit_work_time_minutes`            | `integer` | `false`      | e.g. `0`                                                   |


## List workshop orders

List workshop orders for a specific customer

## Get workshop order

Get workshop order

## Create workshop order

Create a workshop order

## Update workshop order

Update a workshop order


