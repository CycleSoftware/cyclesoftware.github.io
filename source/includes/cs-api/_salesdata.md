# Sales data #

Access sales data

***Authentication mechanism***

- Basic HTTP Authentication
- Scopes: `sales-export`

## Sales transactions - V1 ##

This API endpoint is deprecated, please use V2.

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

| URI parameter | Type   | Description              |
|---------------|--------|--------------------------|
| `start_date`  | `date` | end date e.g. 2020-01-01 |
| `end_date`    | `date` | end date e.g. 2020-01-01 |

| GET parameter | Type     | Description                                                                                                                                                 |
|---------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `date_field`  | `string` | `kassadatum` (default) interval as booked date<br/> `datetime_modified` interval as modification dates<br/>`factuurdatum` interval as invoice proforma date |

## Sales transactions - V2 ##

Get sales transactions and related data such as customers, article and object data.
By default the book-date is used.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v2/salesdata/transactions.json?date_field=:date_field&date_start=:date_start&date_end=:date_end&only_booked_transactions=:only_booked_transactions&store_id=:store_id&dealer_ids=:dealer_ids</h6>
	</div>
</div>
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v2/salesdata/transactions.json?token=:pagination_token</h6>
	</div>
</div>

| GET parameter              | Type      | Description                                                                                                                                                                          |
|----------------------------|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `date_field`               | `?string` | Type of date field `book_date`,`modified_at`, `transaction_date`, defaults to `book_date`                                                                                            |
| `date_start`               | `?date`   | Start date of interval for date_field e.g. `2024-01-01`                                                                                                                              |
| `date_end`                 | `?date`   | End date of interval for date_field e.g. `2024-01-01`                                                                                                                                |
| `only_booked_transactions` | `?bool`   | If `true` only `final` / `booked` transactions will be given                                                                                                                         |
| `store_id`                 | `?int`    | Store ID for filtering                                                                                                                                                               |
| `dealer_ids`               | `?string` | CSV of dealer_ids (only applicable for `warehouse` accounts), dealer_ids are converted to account to get all data from that account                                                  |
| `sales_order_ids`          | `?string` | Filter sales transaction on a CSV of sales order IDs e.g. `1000,2000`. Max 25 sales-order-ids are allowed. Multiple transactions per `sales_order_id` can be returned (split-orders) |
| `token`                    | `?string` | The token of next result set in pagination. In `pagination.next_url` the full URL for next result set if given if available                                                          |

### Properties

| Property                                                             | Type                   | Description                                                                                                                                      |
|----------------------------------------------------------------------|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| `data`                                                               | `object[]`             | Array with data objects                                                                                                                          |
| `data[].account_id`                                                  | `integer`              | Account ID within CycleSoftware e.g. `1`                                                                                                         |
| `data[].store_id`                                                    | `integer`              | Store ID within account e.g. `1`                                                                                                                 |
| `data[].sales_transaction_number`                                    | `integer`              | Sales transaction number / invoice number e.g. `233233`                                                                                          |
| `data[].type_name`                                                   | `string`               | Type name of transaction e.g. `normaal`                                                                                                          |
| `data[].is_final`                                                    | `boolean`              | `true` when the transaction is booked                                                                                                            |
| `data[].book_location_id`                                            | `?integer`             | Book location ID e.g. `1`                                                                                                                        |
| `data[].transaction_date`                                            | `date`                 | Transaction date e.g. `2009-08-17`                                                                                                               |
| `data[].created_at`                                                  | `datetime`             | Creation date-time e.g. `2009-08-17 00:00:00`                                                                                                    |
| `data[].modified_at`                                                 | `datetime`             | Modified date-time e.g. `2016-06-27 09:12:39`                                                                                                    |
| `data[].booked_at`                                                   | `?datetime`            | Book date time e.g. `2009-08-17 15:24:00`                                                                                                        |
| `data[].vat_number`                                                  | `?string`              | VAT-number of customer                                                                                                                           |
| `data[].vat_country_code`                                            | `?string`              | VAT country code if VAT from other country is applied                                                                                            |
| `data[].total_amount_cents`                                          | `integer`              | Total amount in cents of the transaction e.g. `99900`                                                                                            |
| `data[].unpayed_amount_cents`                                        | `integer`              | Total amount that is unpayed e.g. `5000`                                                                                                         |
| `data[].sales_employee_name`                                         | `string`               | Employee name of sales person e.g. `John`                                                                                                        |
| `data[].sales_employee_id`                                           | `integer`              | Employee ID of sales person e.g. `3`                                                                                                             |
| `data[].booked_by_employee_name`                                     | `string`               | Employee name who booked the transaction e.g. `John`                                                                                             |
| `data[].booked_by_employee_id`                                       | `integer`              | Employee ID who booked the transaction e.g. `3`                                                                                                  |
| `data[].last_update_by_employee_name`                                | `string`               | Employee name who last updated the transaction e.g. `John`                                                                                       |
| `data[].last_update_by_employee_id`                                  | `integer`              | Employee ID who last updated the transaction e.g. `3`                                                                                            |
| `data[].customer_phone_number_id`                                    | `?string`              | Preferred phone number ID of customer for communication e.g. `mob`                                                                               |
| `data[].customer`                                                    | `?object`              | Object with customer details if known `null` otherwise. See Customer (object)                                                                    |
| `data[].debit_sales_transaction_number`                              | `?integer`             | If transaction is a credit this is referring to the debit transaction e.g. `1199`                                                                |
| `data[].credit_sales_transaction_number`                             | `?integer`             | If transaction has a credit this is referring to the credit transaction e.g. `1199`                                                              |
| `data[].sales_order`                                                 | `?object`              | Object with information about the sales order                                                                                                    |
| `data[].sales_order.delivery_method_id`                              | `integer`              | Delivery method ID e.g. `0` (see common enum `delivery_methods`)                                                                                 |
| `data[].sales_order.reference_id`                                    | `string`               | Reference ID of the sales order                                                                                                                  |
| `data[].sales_order.reference_text`                                  | `string`               | Reference text of the sales order                                                                                                                |
| `data[].sales_order.sales_order_id`                                  | `integer`              | Sales order ID `48143`                                                                                                                           |
| `data[].sales_order.sales_order_status_id`                           | `integer`              | Sales order status ID e.g. `9` (see common enum `sales_order_status`)                                                                            |
| `data[].sales_order.sales_order_type_id`                             | `integer`              | Sales order type  ID e.g. `6` (see common enum `sales_order_types`)                                                                              |
| `data[].sales_order.track_trace_reference`                           | `string`               | Track and trace reference                                                                                                                        |
| `data[].workshop_order`                                              | `?object`              | Workshop / repair related information                                                                                                            |
| `data[].workshop_order.workshop_order_id`                            | `integer`              | Workshop order ID e.g. `40573`                                                                                                                   |
| `data[].workshop_order.repair_object_id`                             | `integer`              | Repair object ID e.g. `425`                                                                                                                      |
| `data[].workshop_order.workshop_order_type_id`                       | `integer`              | Workshop type ID e.g. `1` (see common enum `workshop_order_types`)                                                                               |
| `data[].workshop_order.workshop_order_status_id`                     | `integer`              | Workshop status ID e.g. `8` (see common enum `workshop_order_status`)                                                                            |
| `data[].workshop_order.workshop_rate_id`                             | `integer`              | Workshop rate ID e.g. `1` (see common enum `workshop_rates`)                                                                                     |
| `data[].workshop_order.mechanic_employee_id`                         | `?integer`             | Workshop mechanic ID e.g. `1` (see employees endpoint) if available                                                                              |
| `data[].workshop_order.mechanic_employee_name`                       | `?string`              | Workshop mechanic name e.g. `John` if available                                                                                                  |
| `data[].workshop_order.delivery_method_id`                           | `integer`              | Delivery method ID e.g. `0` (see common enum `delivery_methods`)                                                                                 |
| `data[].workshop_order.reference_text`                               | `string`               | Reference of order e.g. `85`                                                                                                                     |
| `data[].workshop_order.km_age`                                       | `?integer`             | KM age of object if registered with this order                                                                                                   |
| `data[].workshop_order.object`                                       | `object`               | Information about of repair object                                                                                                               |
| `workshop_order.object.color`                                        | `string`               | Color of repair object e.g. `Zwart`                                                                                                              |
| `workshop_order.object.brand_name`                                   | `string`               | Brand of repair object e.g. `Batavus`                                                                                                            |
| `workshop_order.object.model_name`                                   | `string`               | Model name of repair object e.g. `Cosmo CS 1`                                                                                                    |
| `workshop_order.object.object_id`                                    | `integer`              | Object ID of repair object e.g. `16782`                                                                                                          |
| `workshop_order.object.size`                                         | `string`               | Size description of repair object e.g. `L`                                                                                                       |
| `workshop_order.object.year`                                         | `?int`                 | Model year of repair object or `null`                                                                                                            |
| `data[].workshop_order.identification`                               | `object`               | Identifications of repair object                                                                                                                 |
| `workshop_order.identification.battery_number`                       | `?string`              | The battery number if set                                                                                                                        |
| `workshop_order.identification.battery_number_2`                     | `?string`              | The battery number_2 if set                                                                                                                      |
| `workshop_order.identification.engine_number`                        | `?string`              | The engine number if set                                                                                                                         |
| `workshop_order.identification.frame_number`                         | `?string`              | The frame number if set                                                                                                                          |
| `workshop_order.identification.imei_number`                          | `?string`              | The imei number if set                                                                                                                           |
| `workshop_order.identification.key_number`                           | `?string`              | The key number if set                                                                                                                            |
| `workshop_order.identification.key_number_2`                         | `?string`              | The key number_2 if set                                                                                                                          |
| `workshop_order.identification.license_plate_number`                 | `?string`              | The license plat if set if se                                                                                                                    |
| `workshop_order.identification.lock_number`                          | `?string`              | The lock number if set                                                                                                                           |
| `workshop_order.identification.lock_number_2`                        | `?string`              | The lock number_2 if set                                                                                                                         |
| `workshop_order.identification.serial_number`                        | `?string`              | The serial number if set                                                                                                                         |
| `workshop_order.identification.velopass_code`                        | `?string`              | The velopass code if set                                                                                                                         |
| `data[].sales_items`                                                 | `object[]`             | Array with sold items                                                                                                                            |
| `data[].sales_items[].sales_item_id`                                 | `integer`              | Unique sales item ID e.g. `63883`                                                                                                                |
| `data[].sales_items[].item_type_id`                                  | `integer`              | Item type ID e.g. `1` (see common enum `item_types`)                                                                                             |
| `data[].sales_items[].pos_group_id`                                  | `integer`              | POS group ID e.g. `1` (see common enum `pos_groups`)                                                                                             |
| `data[].sales_items[].pos_group_name`                                | `string`               | POS group name e.g. `Diversen`                                                                                                                   |
| `data[].sales_items[].barcode`                                       | `string`               | Barcode or article identification e.g. `8713504001924`                                                                                           |
| `data[].sales_items[].quantity`                                      | `integer`              | Number of items sold e.g. `1`                                                                                                                    |
| `data[].sales_items[].gross_unit_price_in_vat_cents`                 | `integer`              | Gross unit price including VAT in cents e.g. `0`                                                                                                 |
| `data[].sales_items[].gross_unit_price_ex_vat_cents`                 | `integer`              | Gross unit price excluding VAT in cents e.g. `0`                                                                                                 |
| `data[].sales_items[].unit_discount_in_vat_cents`                    | `integer`              | Unit discount amount including VAT in cents e.g. `0`                                                                                             |
| `data[].sales_items[].unit_discount_ex_vat_cents`                    | `integer`              | Unit discount amount excluding VAT in cents e.g. `0`                                                                                             |
| `data[].sales_items[].line_discount_in_vat_cents`                    | `integer`              | Line discount amount including VAT in cents .g. `0`                                                                                              |
| `data[].sales_items[].line_discount_ex_vat_cents`                    | `integer`              | Line discount amount excluding VAT in cents e.g. `0`                                                                                             |
| `data[].sales_items[].nett_line_price_in_vat_cents`                  | `integer`              | Nett line price including VAT in cents e.g. `12100`                                                                                              |
| `data[].sales_items[].nett_line_price_ex_vat_cents`                  | `integer`              | Nett line price excluding VAT in cents e.g. `10000`                                                                                              |
| `data[].sales_items[].ex_vat_based_prices`                           | `boolean`              | `true` if the prices were based on the amounts excluding VAT                                                                                     |
| `data[].sales_items[].discount_percentage`                           | `decimal`              | Discount percentage e.g. `10`                                                                                                                    |
| `data[].sales_items[].vat_code`                                      | `integer`              | VAT code e.g. `2` (see common enum `vat_codes`)                                                                                                  |
| `data[].sales_items[].vat_percentage`                                | `integer&vert;decimal` | VAT percentage e.g. `21`                                                                                                                         |
| `data[].sales_items[].vat_amount_cents`                              | `integer`              | Line VAT amount in cents e.g. `21`, for margin VAT always `0`                                                                                    |
| `data[].sales_items[].purchase_price_ex_vat_cents`                   | `?integer`             | Purchase price recorded on creation of `sales_item` e.g. `4900`                                                                                  |
| `data[].sales_items[].description`                                   | `string`               | Sales item description e.g. `Cyclon All weather spray 250ml`                                                                                     |
| `data[].sales_items[].description_extended`                          | `?string`              | Extended description e.g. `Something extra`                                                                                                      |
| `data[].sales_items[].article`                                       | `?object`              | Object with sold article information                                                                                                             |
| `data[].sales_items[].article.brand_name`                            | `string`               | Brand name from article details e.g. `CYCLON`                                                                                                    |
| `data[].sales_items[].article.description`                           | `string`               | Article description for article details or first supplier e.g. `Cyclon All weather spray 250ml`                                                  |
| `data[].sales_items[].article.dst_main_id`                           | `?string`              | DST category ID e.g. `2`                                                                                                                         |
| `data[].sales_items[].article.dst_main_name`                         | `?string`              | DST category name e.g. `O&A`                                                                                                                     |
| `data[].sales_items[].article.dst_sub_id`                            | `?string`              | DST sub category ID e.g. `N`                                                                                                                     |
| `data[].sales_items[].article.dst_sub_name`                          | `?string`              | DST sub category name e.g. `Onderdelen/Reparatie`                                                                                                |
| `data[].sales_items[].article.dst_sub_sub_id`                        | `?string`              | DST sub-sub category ID e.g. `8`                                                                                                                 |
| `data[].sales_items[].article.dst_sub_sub_name`                      | `?string`              | DST sub-sub category name e.g. `Smeer-, poets- en onderhoudsmiddelen`                                                                            |
| `data[].sales_items[].article.sales_price_cents`                     | `integer`              | Recommended retail price in cents set in article details or determined from first supplier e.g. `1375`                                           |
| `data[].sales_items[].article.purchase_price_ex_vat_cents`           | `integer`              | Purchase price in cents set in article details or determined from first supplier e.g. `688`                                                      |
| `data[].sales_items[].article.suppliers`                             | `object[]`             | List of suppliers for article (priority sorted)                                                                                                  |
| `data[].sales_items[].article.suppliers[].supplier_id`               | `integer`              | Supplier ID e.g. `2` (see common suppliers endpoint)                                                                                             |
| `data[].sales_items[].article.suppliers[].supplier_name`             | `string`               | Supplier name e.g. `Kruitbosch`                                                                                                                  |
| `data[].sales_items[].article.suppliers[].article_id`                | `string`               | Article number `CCS250`                                                                                                                          |
| `data[].sales_items[].article.suppliers[].purchase_price_cents`      | `integer`              | Gross purchase price in cents e.g. `688`                                                                                                         |
| `data[].sales_items[].article.suppliers[].rrp_cents`                 | `integer`              | Recommended retail price in cents e.g. `1375`                                                                                                    |
| `data[].sales_items[].object`                                        | `?object`              | Sold object information, may be `null` if not related to an object                                                                               |
| `data[].sales_items[].object.object_id`                              | `integer`              | Unique object ID within account e.g. `15651`                                                                                                     |
| `data[].sales_items[].object.object_barcode`                         | `string`               | Internal barcode e.g. `F23232323`                                                                                                                |
| `data[].sales_items[].object.barcode`                                | `string`               | Barcode of article e.g. `8723723723`                                                                                                             |
| `data[].sales_items[].object.article_id`                             | `string`               | Article number e.g. `A2323`                                                                                                                      |
| `data[].sales_items[].object.object_type_id`                         | `integer`              | Object type e.g. `1` Bike `2` Moped                                                                                                              |
| `data[].sales_items[].object.is_demo`                                | `boolean`              | `true` if demo-bike                                                                                                                              |
| `data[].sales_items[].object.stock_location_name`                    | `string`               | Stock location name e.g. `store-floor`                                                                                                           |
| `data[].sales_items[].object.brand_name`                             | `string`               | Brand description e.g. `Giant`                                                                                                                   |
| `data[].sales_items[].object.brand_id`                               | `integer`              | Brand / supplier ID e.g. `2121` (see common suppliers endpoint)                                                                                  |
| `data[].sales_items[].object.model_name`                             | `string`               | Model name e.g. `Foxx`                                                                                                                           |
| `data[].sales_items[].object.category_name`                          | `string`               | Category description e.g. `Stadsfietsen`                                                                                                         |
| `data[].sales_items[].object.is_elo_bike`                            | `boolean`              | Electric bike e.g. `false`                                                                                                                       |
| `data[].sales_items[].object.frame_type`                             | `string`               | Frame type e.g. `Jongens`                                                                                                                        |
| `data[].sales_items[].object.color`                                  | `string`               | Color e.g. `Blauw`                                                                                                                               |
| `data[].sales_items[].object.basic_color`                            | `string`               | Basic color description e.g. `BLUE`                                                                                                              |
| `data[].sales_items[].object.basic_color_secondary`                  | `string`               | 2nd Basic color description e.g. `BLACK`                                                                                                         |
| `data[].sales_items[].object.year`                                   | `integer`              | Model year e.g. `2023` //@TODO NULL?                                                                                                             |
| `data[].sales_items[].object.object_status`                          | `string`               | Status description new vs used e.g. `Gebruikt`                                                                                                   |
| `data[].sales_items[].object.size`                                   | `?string`              | Size e.g. `Meisjes 20`                                                                                                                           |
| `data[].sales_items[].object.frame_height`                           | `string`               | Frame height in cm e.g. `38`                                                                                                                     |
| `data[].sales_items[].object.wheel_size`                             | `?string`              | Wheel size inches e.g. `24`                                                                                                                      |
| `data[].sales_items[].object.frame_size_supplier`                    | `string`               | Frame size description supplier e.g. `L`                                                                                                         |
| `data[].sales_items[].object.tyre_size`                              | `?string`              | Tyre size description                                                                                                                            |
| `data[].sales_items[].object.material_description`                   | `string`               | Description of material e.g. `CARBON`                                                                                                            |
| `data[].sales_items[].object.gross_weight_kg`                        | `?decimal`             | Gross weight e.g. `20`                                                                                                                           |
| `data[].sales_items[].object.weight_kg`                              | `?decimal`             | Weight e.g. `17`                                                                                                                                 |
| `data[].sales_items[].object.gear_count`                             | `?integer`             | Number of gears e.g. `20`                                                                                                                        |
| `data[].sales_items[].object.description_extra`                      | `string`               | Extra description e.g. `Some text`                                                                                                               |
| `data[].sales_items[].object.ecommerce_price_cents`                  | `integer`              | E-commerce price in cents e.g. `999900`                                                                                                          |
| `data[].sales_items[].object.road_worthy_costs_cents`                | `integer`              | Costs for making road worthy in cents e.g. `0`                                                                                                   |
| `data[].sales_items[].object.internal_workshop_costs_ex_vat_cents`   | `?integer`             | Costs made in internal workshop in cents                                                                                                         |
| `data[].sales_items[].object.purchased_from_customer_id`             | `integer`              | If purchased from a customer, this is the customer id e.g. `4071`                                                                                |
| `data[].sales_items[].object.description`                            | `string`               | Description e.g. `Some text to desribe`                                                                                                          |
| `data[].sales_items[].object.supplier_order_reference`               | `?string`              | Supplier order reference e.g. `12435647`                                                                                                         |
| `data[].sales_items[].object.supplier_invoice_reference`             | `?string`              | Supplier invoice reference e.g. `INV322323`                                                                                                      |
| `data[].sales_items[].object.kilometer_age`                          | `integer`              | KM age of object e.g. `0`                                                                                                                        |
| `data[].sales_items[].object.consignment_status`                     | `integer`              | Consignment status see see common enum for list e.g. `0`                                                                                         |
| `data[].sales_items[].identification`                                | `?object`              | Object with identification such as serial numbers                                                                                                |
| `data[].sales_items[].identification.stock_object_id`                | `integer`              | Unique stock object ID within account e.g. `15651`                                                                                               |
| `data[].sales_items[].identification.frame_number`                   | `?string`              | Frame number e.g. `WOW238C`                                                                                                                      |
| `data[].sales_items[].identification.key_number`                     | `?string`              | Key number e.g. `97804`                                                                                                                          |
| `data[].sales_items[].identification.key_number_2`                   | `?string`              | Key number 2 e.g. `97804-2`                                                                                                                      |
| `data[].sales_items[].identification.lock_number`                    | `?string`              | Lock number e.g. `R334320-08`                                                                                                                    |
| `data[].sales_items[].identification.lock_number_2`                  | `?string`              | Lock number 2 e.g. `R334320-08-2`                                                                                                                |
| `data[].sales_items[].identification.battery_number`                 | `?string`              | Battery number e.g. `BA223432323-1231-08`                                                                                                        |
| `data[].sales_items[].identification.battery_number_2`               | `?string`              | Battery number 2 e.g. `BA223432323-1231-08-2`                                                                                                    |
| `data[].sales_items[].identification.engine_number`                  | `?string`              | Engine number e.g. `E43434343443`                                                                                                                |
| `data[].sales_items[].identification.serial_number`                  | `?string`              | Serial number e.g. `975-0528-1296-2005-06`                                                                                                       |
| `data[].sales_items[].identification.imei_number`                    | `?string`              | IMEI number e.g. `975-0528-1296-2005-06`                                                                                                         |
| `data[].sales_items[].identification.license_plate_number`           | `?string`              | License plate number e.g. `DT-GX-22`                                                                                                             |
| `data[].sales_items[].identification.velopass_code`                  | `?string`              | Velopass code e.g. `VP3D3G4KD3`                                                                                                                  |
| `data[].sales_items[].identification.warehouse_stock_item_id`        | `?integer`             | For warehouse accounts the stock item ID if known e.g. `1000`                                                                                    |
| `data[].sales_items[].identification.warehouse_outbound_shipment_id` | `?integer`             | For warehouse accounts the outbound shipment ID if known e.g. `10033`                                                                            |
| `pagination.next_url`                                                | `?string`              | URL to next result set `null` if no more data  e.g. `https://api.cyclesoftware.nl/api/v2/salesdata/transactions.json?token=NDA3MzcwNT....lBVmUw` |

> HTTP request

```http
GET /api/v2/salesdata/transactions.json?date_field=modified_at&date_start=2024-01-01&date_end=2024-01-15&only_booked_transactions=true&store_id=1 HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 19744

{
    "data": [
        {
            "account_id": 1,
            "store_id": 1,
            "sales_transaction_number": 22222890,
            "type_name": "reparatie",
            "is_final": true,
            "book_location_id": 1,
            "transaction_date": "2023-01-22",
            "created_at": "2023-01-22 11:52:57",
            "modified_at": "2023-02-09 18:29:01",
            "booked_at": "2023-02-09 18:29:01",
            "vat_number": null,
            "vat_country_code": null,
            "total_amount_cents": 18994,
            "unpayed_amount_cents": 0,
            "sales_employee_name": "Sander",
            "sales_employee_id": 49075,
            "booked_by_employee_name": "Giel",
            "booked_by_employee_id": 1001,
            "last_update_by_employee_name": "Giel",
            "last_update_by_employee_id": 1001,
            "customer_phone_number_id": "mob",
            "customer": {
                "customer_id": 235268968,
                "customer_full_name": "Sander",
                "street": "Langeveld",
                "housenumber": "12",
                "housenumber_postfix": "",
                "city": "Het dorp",
                "postcode": "3420",
                "country": "BE",
                "loyalty_points": 430,
                "email": "sander@example.nl",
                "global_discount": 0,
                "country_code": "BE",
                "iban": "",
                "date_of_birth": null,
                "phone_numbers": [
                    {
                        "phone_number_id": "mob",
                        "phone_number": "0412345678",
                        "name": "Basis mobiel"
                    }
                ],
                "language_code": "nl_NL"
            },
            "sales_order": {
                "sales_order_id": 55339,
                "sales_order_type_id": 6,
                "sales_order_status_id": 9,
                "reference_id": "",
                "reference_text": "",
                "delivery_method_id": 0,
                "track_trace_reference": ""
            },
            "workshop_order": {
                "workshop_order_id": 55339,
                "repair_object_id": 19224,
                "workshop_order_type_id": 1,
                "workshop_order_status_id": 8,
                "workshop_rate_id": 1,
                "delivery_method_id": 0,
                "reference_text": "",
                "km_age": null,
                "object": {
                      "brand_name": "Giant",
                      "color": "Zwart",
                      "model_name": "Cosmo CS 1",
                      "object_id": 19224,
                      "size": "L",
                      "year": 2019
                },
                "identification": {
                     "battery_number": "BATT3333",
                     "battery_number_2": null,
                     "engine_number": null,
                     "frame_number": "FR12121212",
                     "imei_number": null,
                     "key_number": null,
                     "key_number_2": null,
                     "license_plate_number": null,
                     "lock_number": null,
                     "lock_number_2": null,
                     "serial_number": null,
                     "velopass_code": null
              },
            },
            "sales_items": [
                {
                    "sales_item_id": 170603180,
                    "item_type_id": 11,
                    "pos_group_id": 2,
                    "pos_group_name": "Reparatie",
                    "barcode": null,
                    "quantity": 1,
                    "gross_unit_price_in_vat_cents": 13000,
                    "gross_unit_price_ex_vat_cents": 11927,
                    "unit_discount_in_vat_cents": 0,
                    "unit_discount_ex_vat_cents": 0,
                    "line_discount_in_vat_cents": 0,
                    "line_discount_ex_vat_cents": 0,
                    "nett_line_price_in_vat_cents": 13000,
                    "nett_line_price_ex_vat_cents": 11927,
                    "ex_vat_based_prices": false,
                    "discount_percentage": null,
                    "vat_code": 1,
                    "vat_percentage": 9,
                    "vat_amount_cents": 1073,
                    "purchase_price_ex_vat_cents": null,
                    "description": "Reparatie",
                    "description_extended": null,
                    "article": null,
                    "object": null,
                    "identification": null
                },
                {
                    "sales_item_id": 170603182,
                    "item_type_id": 1,
                    "pos_group_id": 21,
                    "pos_group_name": "Onderdelen",
                    "barcode": "8710177990203",
                    "quantity": 1,
                    "gross_unit_price_in_vat_cents": 2095,
                    "gross_unit_price_ex_vat_cents": 1731,
                    "unit_discount_in_vat_cents": -904,
                    "unit_discount_ex_vat_cents": -747,
                    "line_discount_in_vat_cents": -747,
                    "line_discount_ex_vat_cents": -747,
                    "nett_line_price_in_vat_cents": 2999,
                    "nett_line_price_ex_vat_cents": 2479,
                    "ex_vat_based_prices": false,
                    "discount_percentage": null,
                    "vat_code": 2,
                    "vat_percentage": 21,
                    "vat_amount_cents": 520,
                    "purchase_price_ex_vat_cents": null,
                    "description": "Jumbo pomp op plank met slang",
                    "description_extended": null,
                    "article": {
                        "brand_name": "Jumbo",
                        "description": "POMP JUMBO VOET M/PLANK+SLANG",
                        "dst_main_id": "2",
                        "dst_main_name": "O&A",
                        "dst_sub_id": "I",
                        "dst_sub_name": "Pompen",
                        "dst_sub_sub_id": "1",
                        "dst_sub_sub_name": "Voetpomp",
                        "sales_price_cents": 2500,
                        "purchase_price_ex_vat_cents": 100,
                        "suppliers": [
                            {
                                "supplier_id": 5229,
                                "supplier_name": "Accell NL",
                                "article_id": "650353",
                                "purchase_price_cents": 100,
                                "rrp_cents": 1815
                            },
                            {
                                "supplier_id": 1,
                                "supplier_name": "Agu",
                                "article_id": "131026",
                                "purchase_price_cents": 100,
                                "rrp_cents": 2995
                            },
                            {
                                "supplier_id": 117,
                                "supplier_name": "Aalten B.V.",
                                "article_id": "46551850",
                                "purchase_price_cents": 100,
                                "rrp_cents": 2695
                            }
                        ]
                    },
                    "object": null,
                    "identification": null
                },
                {
                    "sales_item_id": 170603184,
                    "item_type_id": 1,
                    "pos_group_id": 5,
                    "pos_group_name": "Banden",
                    "barcode": "8714692239588",
                    "quantity": 1,
                    "gross_unit_price_in_vat_cents": 2995,
                    "gross_unit_price_ex_vat_cents": 2475,
                    "unit_discount_in_vat_cents": 2995,
                    "unit_discount_ex_vat_cents": 2475,
                    "line_discount_in_vat_cents": 2475,
                    "line_discount_ex_vat_cents": 2475,
                    "nett_line_price_in_vat_cents": 0,
                    "nett_line_price_ex_vat_cents": 0,
                    "ex_vat_based_prices": false,
                    "discount_percentage": 100,
                    "vat_code": 2,
                    "vat_percentage": 21,
                    "vat_amount_cents": 0,
                    "purchase_price_ex_vat_cents": 100,
                    "description": "23-622 Band vouw zwart 28919 Vredestein",
                    "description_extended": null,
                    "article": {
                        "brand_name": "VREDESTEIN",
                        "description": "23-622 Band vouw zwart 28919 Vredestein",
                        "dst_main_id": "2",
                        "dst_main_name": "O&A",
                        "dst_sub_id": "A",
                        "dst_sub_name": "Banden",
                        "dst_sub_sub_id": "2",
                        "dst_sub_sub_name": "Buitenbanden/tubes",
                        "sales_price_cents": 2995,
                        "purchase_price_ex_vat_cents": 100,
                        "suppliers": [
                            {
                                "supplier_id": 5229,
                                "supplier_name": "Accell NL",
                                "article_id": "685167",
                                "purchase_price_cents": 100,
                                "rrp_cents": 2995
                            }
                        ]
                    },
                    "object": null,
                    "identification": null
                },
                {
                    "sales_item_id": 170603186,
                    "item_type_id": 1,
                    "pos_group_id": 5,
                    "pos_group_name": "Banden",
                    "barcode": "8714692239588",
                    "quantity": 1,
                    "gross_unit_price_in_vat_cents": 2995,
                    "gross_unit_price_ex_vat_cents": 2475,
                    "unit_discount_in_vat_cents": 0,
                    "unit_discount_ex_vat_cents": 0,
                    "line_discount_in_vat_cents": 0,
                    "line_discount_ex_vat_cents": 0,
                    "nett_line_price_in_vat_cents": 2995,
                    "nett_line_price_ex_vat_cents": 2475,
                    "ex_vat_based_prices": false,
                    "discount_percentage": null,
                    "vat_code": 2,
                    "vat_percentage": 21,
                    "vat_amount_cents": 520,
                    "purchase_price_ex_vat_cents": 100,
                    "description": "23-622 Band vouw zwart 28919 Vredestein",
                    "description_extended": null,
                    "article": {
                        "brand_name": "VREDESTEIN",
                        "description": "23-622 Band vouw zwart 28919 Vredestein",
                        "dst_main_id": "2",
                        "dst_main_name": "O&A",
                        "dst_sub_id": "A",
                        "dst_sub_name": "Banden",
                        "dst_sub_sub_id": "2",
                        "dst_sub_sub_name": "Buitenbanden/tubes",
                        "sales_price_cents": 2995,
                        "purchase_price_ex_vat_cents": 100,
                        "suppliers": [
                            {
                                "supplier_id": 5229,
                                "supplier_name": "Accell NL",
                                "article_id": "685167",
                                "purchase_price_cents": 100,
                                "rrp_cents": 2995
                            },
                            {
                                "supplier_id": 8,
                                "supplier_name": "Rutteman",
                                "article_id": "23vr622fiopz",
                                "purchase_price_cents": 100,
                                "rrp_cents": 2995
                            }
                        ]
                    },
                    "object": null,
                    "identification": null
                }
            ]
        },
        {
            "account_id": 1,
            "store_id": 1,
            "sales_transaction_number": 22222924,
            "type_name": "fiets",
            "is_final": true,
            "book_location_id": 1,
            "transaction_date": "2023-01-27",
            "created_at": "2023-01-27 09:52:52",
            "modified_at": "2023-02-06 16:41:29",
            "booked_at": "2023-02-06 16:40:05",
            "vat_number": null,
            "vat_country_code": null,
            "total_amount_cents": 831150,
            "unpayed_amount_cents": 798400,
            "sales_employee_name": "Sander",
            "sales_employee_id": 49075,
            "booked_by_employee_name": "David",
            "booked_by_employee_id": 65043,
            "last_update_by_employee_name": "David",
            "last_update_by_employee_id": 65043,
            "customer_phone_number_id": "mob",
            "customer": {
                "customer_id": 235270696,
                "customer_full_name": "John",
                "street": "Betelgeuze",
                "housenumber": "122",
                "housenumber_postfix": "",
                "city": "Utrecht",
                "postcode": "3322AW",
                "country": "NL",
                "loyalty_points": 5000,
                "email": "robin@example.nl",
                "global_discount": 0,
                "country_code": "NL",
                "iban": "",
                "date_of_birth": "2000-01-01",
                "phone_numbers": [
                    {
                        "phone_number_id": "mob",
                        "phone_number": "06-12650321",
                        "name": "Basis mobiel"
                    },
                    {
                        "phone_number_id": "816991",
                        "phone_number": "0612650321",
                        "name": "test"
                    }
                ],
                "language_code": "nl_NL"
            },
            "sales_order": null,
            "workshop_order": null,
            "sales_items": [
                {
                    "sales_item_id": 170918009,
                    "item_type_id": 2,
                    "pos_group_id": 1,
                    "pos_group_name": "Fietsen",
                    "barcode": "4712878754607",
                    "quantity": 1,
                    "gross_unit_price_in_vat_cents": 829900,
                    "gross_unit_price_ex_vat_cents": 761376,
                    "unit_discount_in_vat_cents": 0,
                    "unit_discount_ex_vat_cents": 0,
                    "line_discount_in_vat_cents": 0,
                    "line_discount_ex_vat_cents": 0,
                    "nett_line_price_in_vat_cents": 829900,
                    "nett_line_price_ex_vat_cents": 761376,
                    "ex_vat_based_prices": false,
                    "discount_percentage": null,
                    "vat_code": 1,
                    "vat_percentage": 9,
                    "vat_amount_cents": 68524,
                    "purchase_price_ex_vat_cents": 10000,
                    "description": "GIANT Stormguard E+, Hematite, XL, XL, 2023, FR000004",
                    "description_extended": null,
                    "article": {
                        "brand_name": "GIANT",
                        "description": "GIANT Stormguard E+ Hematite XL 2023",
                        "dst_main_id": 1,
                        "dst_main_name": "Fietsen",
                        "dst_sub_id": "F",
                        "dst_sub_name": "Crosshybrides",
                        "dst_sub_sub_id": 1,
                        "dst_sub_sub_name": "Crosshybride (elektrisch)",
                        "sales_price_cents": 829900,
                        "purchase_price_ex_vat_cents": 10000,
                        "suppliers": [
                            {
                                "supplier_id": 2121,
                                "supplier_name": "Giant",
                                "article_id": "2203712108",
                                "purchase_price_cents": 10000,
                                "rrp_cents": 829900
                            }
                        ]
                    },
                    "object": {
                        "object_id": 34614,
                        "object_barcode": "",
                        "barcode": "4712878754607",
                        "article_id": "2203712108",
                        "object_type_id": 1,
                        "is_demo": false,
                        "stock_location_name": "",
                        "brand_name": "GIANT",
                        "brand_id": 2121,
                        "model_name": "Stormguard E+",
                        "category_name": "Crosshybrides - elektrisch",
                        "is_elo_bike": true,
                        "frame_type": "UNI",
                        "color": "Hematite",
                        "basic_color": "",
                        "basic_color_secondary": "",
                        "year": 2023,
                        "object_status": "Nieuw",
                        "size": "XL",
                        "frame_height": null,
                        "wheel_size": "27",
                        "frame_size_supplier": "XL",
                        "tyre_size": null,
                        "material_description": "ALUMINIUM",
                        "gross_weight_kg": 38,
                        "weight_kg": 30,
                        "gear_count": 999,
                        "description_extra": "Stormguard E+ 1 25km/h XL Hematite/Black",
                        "ecommerce_price_cents": 829900,
                        "road_worthy_costs_cents": 0,
                        "internal_workshop_costs_ex_vat_cents": null,
                        "purchased_from_customer_id": 0,
                        "description": "Stormguard E+ 1 25km/h",
                        "supplier_order_reference": null,
                        "supplier_invoice_reference": null,
                        "kilometer_age": 0,
                        "consignment_status": 0
                    },
                    "identification": {
                        "stock_object_id": 34614,
                        "frame_number": "FR000004",
                        "key_number": null,
                        "key_number_2": null,
                        "lock_number": null,
                        "lock_number_2": null,
                        "battery_number": null,
                        "battery_number_2": null,
                        "engine_number": null,
                        "serial_number": null,
                        "imei_number": null,
                        "license_plate_number": null,
                        "velopass_code": null
                    }
                },
                {
                    "sales_item_id": 170918011,
                    "item_type_id": 1,
                    "pos_group_id": 26,
                    "pos_group_name": "Verwijderingsbijdrage",
                    "barcode": null,
                    "quantity": 1,
                    "gross_unit_price_in_vat_cents": 1250,
                    "gross_unit_price_ex_vat_cents": 1033,
                    "unit_discount_in_vat_cents": 0,
                    "unit_discount_ex_vat_cents": 0,
                    "line_discount_in_vat_cents": 0,
                    "line_discount_ex_vat_cents": 0,
                    "nett_line_price_in_vat_cents": 1250,
                    "nett_line_price_ex_vat_cents": 1033,
                    "ex_vat_based_prices": false,
                    "discount_percentage": null,
                    "vat_code": 2,
                    "vat_percentage": 21,
                    "vat_amount_cents": 217,
                    "purchase_price_ex_vat_cents": null,
                    "description": "Verwijderingsbijdrage accu",
                    "description_extended": null,
                    "article": null,
                    "object": null,
                    "identification": null
                }
            ]
        }
    ],
    "pagination": {
        "next_url": "https://api.cyclesoftware.nl/api/v2/salesdata/transactions.json?token=...."
    }
}
```

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
| `reference_id`            | `string`  | Reference ID `0`                                                           |
| `policy_number`           | `string`  | Policy Number (if available) `12212`                                       |
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
        "reference_id": "0",
        "policy_number": "143123238",
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
        "reference_id": "0",
        "policy_number": "0",
        "insurance_starting_date": "01-04-2022",
        "description": "E-bike casco compleet jaarpremie Aut. Incasso",
        "policy_costs": 650,
        "insured_amount": 176900,
        "premium_amount": 7343
    }
]
```
