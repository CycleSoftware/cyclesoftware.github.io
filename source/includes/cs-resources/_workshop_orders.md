# Workshop orders #

Read, create or update workshop orders

***Scope(s)***

- `resources`

## Workshop order (object)

| **Property**                                      | **Type**   | **Nullable** | **Description**                                                                  |
|---------------------------------------------------|------------|--------------|----------------------------------------------------------------------------------|
| `workshop_order_id`                               | `integer`  | `false`      | Workshop order ID e.g. `978070`                                                  |
| `sales_order_id`                                  | `integer`  | `false`      | Sales order ID e.g. `978070`                                                     |
| `customer_id`                                     | `integer`  | `false`      | Customer ID e.g. `24`                                                            |
| `store_id`                                        | `integer`  | `false`      | Store ID e.g. `1`                                                                |
| `repair_object_id`                                | `integer`  | `false`      | Repair object ID e.g. `1105`                                                     |
| `is_active`                                       | `boolean`  | `false`      | If deleted `false`                                                               |
| `reference_text`                                  | `string`   | `false`      | Own reference e.g. `work_number`                                                 |
| `datetime_scheduled_start`                        | `datetime` | `false`      | Scheduled start e.g. `2023-03-07 12:13:47`                                       |
| `datetime_scheduled_finished`                     | `datetime` | `false`      | Scheduled finished e.g. `2023-03-07 12:43:47`                                    |
| `datetime_created`                                | `datetime` | `false`      | Created at e.g. `2023-03-07 12:13:47`                                            |
| `datetime_modified`                               | `datetime` | `false`      | Modified at e.g. `2023-03-07 12:13:47`                                           |
| `mechanic_employee_id`                            | `integer`  | `false`      | Employee ID of mechanic (see common employees) e.g. `12`                         |
| `created_by_employee_id`                          | `integer`  | `false`      | Created by employee ID (see common employees) e.g. `1`                           |
| `last_update_employee_id`                         | `integer`  | `false`      | Last update by employee ID (see common employees) e.g. `1`                       |
| `phone_number_id`                                 | `string`   | `false`      | Phone number ID for communication e.g. `tel`                                     |
| `repair_description`                              | `string`   | `false`      | Description of repair e.g. `posted repair`                                       |
| `status_id`                                       | `integer`  | `false`      | Status see common enum `workshop_order_status` e.g. `7`                          |
| `status_text`                                     | `string`   | `false`      | Status text see common enum `workshop_order_status` e.g. `Reparatie voltooid`    |
| `invoice_number`                                  | `integer`  | `false`      | Sales transaction / invoice number `0` if not invoiced                           |
| `borrowed_object_reference`                       | `string`   | `false`      | Borrowed object reference                                                        |
| `total_repair_time_minutes`                       | `integer`  | `false`      | Total repair time scheduled in minutes e.g. `30`                                 |
| `custom_repair_time_minutes`                      | `integer`  | `false`      | Custom repair time (total time - repair codes time) e.g. `30`                    |
| `repair_codes`                                    | `string[]` | `true`       | On create a list of repair codes. See repair-codes endpoint                      |
| `service_card_codes`                              | `string[]` | `true`       | On create a list of service-item codes. See service-items endpoint               |
| `delivery_method_id`                              | `integer`  | `false`      | Delivery method see common enum `delivery_methods` e.g. `0`                      |
| `order_items`                                     | `array`    | `false`      | Array of order items                                                             |
| `order_items[].item_id`                           | `integer`  | `false`      | Unique item id within the order e.g. `2`                                         |
| `order_items[].item_type_id`                      | `integer`  | `false`      | Order item type see common enum `transaction_item_types` e.g. `1`                |
| `order_items[].special_type_id`                   | `integer`  | `false`      | Related id for example object id e.g. `0`                                        |
| `order_items[].quantity`                          | `integer`  | `false`      | Quantity e.g. `1`                                                                |
| `order_items[].barcode`                           | `string`   | `false`      | Barcode of item e.g. `102`                                                       |
| `order_items[].pos_group_id`                      | `integer`  | `false`      | POS group see common enum `pos_groups` e.g. `2`                                  |
| `order_items[].description`                       | `string`   | `false`      | Description of item e.g. `In- en uitbouwen electromotor in- en uitbouwen accu`   |
| `order_items[].unit_price_in_vat_cents`           | `integer`  | `false`      | Gross unit price including vat in cents e.g. `9000`                              |
| `order_items[].unit_discount_amount_in_vat_cents` | `integer`  | `false`      | Unit discount amount including VAT in cents e.g. `0`                             |
| `order_items[].price_in_vat_cents`                | `integer`  | `false`      | Line price including VAT in cents e.g. `9000`                                    |
| `order_items[].discount_percentage`               | `decimal`  | `false`      | Discount percentage e.g. `0`                                                     |
| `order_items[].vat_code`                          | `integer`  | `false`      | Vat code see common enum `vat_codes` e.g. `1`                                    |
| `order_items[].vat_percentage`                    | `integer`  | `false`      | Vat percentage e.g. `9`                                                          |
| `order_items[].vat_amount_cents`                  | `integer`  | `false`      | Line vat amount in cents e.g. `743`                                              |
| `order_items[].item_status_id`                    | `integer`  | `false`      | Status ID of item see common enum `sales_order_item_status` e.g. `0`             |
| `order_items[].item_status_text`                  | `string`   | `false`      | Status text of item see common enum `sales_order_item_status` e.g. `Geen status` |
| `order_items[].unit_work_time_minutes`            | `integer`  | `false`      | Unit of work time in minutes e.g. `0`                                            |

## List workshop orders

List workshop orders for a specific customer

## Get workshop order

Get workshop order

## Create workshop order

Create a workshop order

## Update workshop order

Update a workshop order


