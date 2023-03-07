# Workshop orders #

Read, create or update workshop orders

***Scope(s)***

- `resources`

## Workshop order (object)

| **Property**                                      | **Type**   | **Nullable** |                            | **Description**                                                                  |
|---------------------------------------------------|------------|--------------|----------------------------|----------------------------------------------------------------------------------|
| `workshop_order_id`                               | `integer`  | `false`      | `readonly`                 | Workshop order ID e.g. `978070`                                                  |
| `sales_order_id`                                  | `integer`  | `false`      | `readonly`                 | Sales order ID e.g. `978070`                                                     |
| `customer_id`                                     | `integer`  | `false`      | `POST`                     | Customer ID e.g. `24`                                                            |
| `store_id`                                        | `integer`  | `false`      | `POST`                     | Store ID e.g. `1`                                                                |
| `repair_object_id`                                | `integer`  | `false`      | `POST`                     | Repair object ID e.g. `1105`                                                     |
| `is_active`                                       | `boolean`  | `false`      | <code>POST&#124;PUT</code> | If deleted `false`                                                               |
| `reference_text`                                  | `string`   | `false`      | `POST`                     | Own reference e.g. `work_number`                                                 |
| `datetime_scheduled_start`                        | `datetime` | `false`      | <code>POST&#124;PUT</code> | Scheduled start e.g. `2023-03-07 12:13:47`                                       |
| `datetime_scheduled_finished`                     | `datetime` | `false`      | `readonly`                 | Scheduled finished e.g. `2023-03-07 12:43:47`                                    |
| `datetime_created`                                | `datetime` | `false`      | `readonly`                 | Created at e.g. `2023-03-07 12:13:47`                                            |
| `datetime_modified`                               | `datetime` | `false`      | `readonly`                 | Modified at e.g. `2023-03-07 12:13:47`                                           |
| `mechanic_employee_id`                            | `integer`  | `false`      | <code>POST&#124;PUT</code> | Employee ID of mechanic (see common employees) e.g. `12`                         |
| `created_by_employee_id`                          | `integer`  | `false`      | `POST`                     | Created by employee ID (see common employees) e.g. `1`                           |
| `last_update_employee_id`                         | `integer`  | `false`      | `POST`                     | Last update by employee ID (see common employees) e.g. `1`                       |
| `phone_number_id`                                 | `string`   | `false`      | `POST`                     | Phone number ID for communication e.g. `tel`                                     |
| `repair_description`                              | `string`   | `false`      | `POST`                     | Description of repair e.g. `posted repair`                                       |
| `status_id`                                       | `integer`  | `false`      | `POST`                     | Status see common enum `workshop_order_status` e.g. `7`                          |
| `status_text`                                     | `string`   | `false`      | `readonly`                 | Status text see common enum `workshop_order_status` e.g. `Reparatie voltooid`    |
| `invoice_number`                                  | `integer`  | `false`      | `readonly`                 | Sales transaction / invoice number `0` if not invoiced                           |
| `borrowed_object_reference`                       | `string`   | `false`      | <code>POST&#124;PUT</code> | Borrowed object reference                                                        |
| `total_repair_time_minutes`                       | `integer`  | `false`      | `readonly`                 | Total repair time scheduled in minutes e.g. `30`                                 |
| `custom_repair_time_minutes`                      | `integer`  | `false`      | `POST`                     | Custom repair time (total time - repair codes time) e.g. `30`                    |
| `repair_codes`                                    | `string[]` | `true`       | `POST`                     | On create a list of repair codes. See repair-codes endpoint                      |
| `service_card_codes`                              | `string[]` | `true`       | `POST`                     | On create a list of service-item codes. See service-items endpoint               |
| `delivery_method_id`                              | `integer`  | `false`      | <code>POST&#124;PUT</code> | Delivery method see common enum `delivery_methods` e.g. `0`                      |
| `order_items`                                     | `array`    | `false`      | <code>POST&#124;PUT</code> | Array of order items                                                             |
| `order_items[].item_id`                           | `integer`  | `false`      | `readonly`                 | Unique item id within the order e.g. `2`                                         |
| `order_items[].item_type_id`                      | `integer`  | `false`      | <code>POST&#124;PUT</code> | Order item type see common enum `transaction_item_types` e.g. `1`                |
| `order_items[].special_type_id`                   | `integer`  | `false`      | <code>POST&#124;PUT</code> | Related id for example object id e.g. `0`                                        |
| `order_items[].quantity`                          | `integer`  | `false`      | <code>POST&#124;PUT</code> | Quantity e.g. `1`                                                                |
| `order_items[].barcode`                           | `string`   | `false`      | <code>POST&#124;PUT</code> | Barcode of item e.g. `102`                                                       |
| `order_items[].pos_group_id`                      | `integer`  | `false`      | <code>POST&#124;PUT</code> | POS group see common enum `pos_groups` e.g. `2`                                  |
| `order_items[].description`                       | `string`   | `false`      | <code>POST&#124;PUT</code> | Description of item e.g. `In- en uitbouwen electromotor in- en uitbouwen accu`   |
| `order_items[].unit_price_in_vat_cents`           | `integer`  | `false`      | <code>POST&#124;PUT</code> | Gross unit price including vat in cents e.g. `9000`                              |
| `order_items[].unit_discount_amount_in_vat_cents` | `integer`  | `false`      | <code>POST&#124;PUT</code> | Unit discount amount including VAT in cents e.g. `0`                             |
| `order_items[].price_in_vat_cents`                | `integer`  | `false`      | <code>POST&#124;PUT</code> | Line price including VAT in cents e.g. `9000`                                    |
| `order_items[].discount_percentage`               | `decimal`  | `false`      | <code>POST&#124;PUT</code> | Discount percentage e.g. `0`                                                     |
| `order_items[].vat_code`                          | `integer`  | `false`      | <code>POST&#124;PUT</code> | Vat code see common enum `vat_codes` e.g. `1`                                    |
| `order_items[].vat_percentage`                    | `integer`  | `false`      | `readonly`                 | Vat percentage e.g. `9`                                                          |
| `order_items[].vat_amount_cents`                  | `integer`  | `false`      | `readonly`                 | Line vat amount in cents e.g. `743`                                              |
| `order_items[].item_status_id`                    | `integer`  | `false`      | <code>POST&#124;PUT</code> | Status ID of item see common enum `sales_order_item_status` e.g. `0`             |
| `order_items[].item_status_text`                  | `string`   | `false`      | `readonly`                 | Status text of item see common enum `sales_order_item_status` e.g. `Geen status` |
| `order_items[].unit_work_time_minutes`            | `integer`  | `false`      | <code>POST&#124;PUT</code> | Unit of work time in minutes e.g. `0`                                            |

## List workshop orders

List workshop orders for a specific customer

## Get workshop order

Get workshop order

## Create workshop order

Create a workshop order

## Update workshop order

Update a workshop order


