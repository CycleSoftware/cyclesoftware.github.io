# Workshop #

Access workshop data

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `warehouse`

## Workshop assemblies ##

Get a list of stock items released for shipment

| GET parameter               | Type      | Description                                                                                                          |
|-------------------------|-----------|----------------------------------------------------------------------------------------------------------------------|
|`start_date`                  | date    | Start date interval (yyyy-mm-dd) <i class="label label-info">required</i>                                                                                                         |
|`end_date`                  | date    | Start date interval (yyyy-mm-dd) <i class="label label-info">required</i>                                                                                                         |
|`offset`                  | integer    | Pagination offset. <i class="label label-info">optional</i>                                                                                                          |

### Properties ###

| Property                         | Type              | Nullable        | Description               |
| -------------------------------- | ----------------- | --------------- | ------------------------- |
| `error`                            | `boolean` | `false` | e.g. `false`      |
| `error_message`                    | `string`    | `true`  | The error message if an error occurred                          |
| `data[].stock_item_id`             | `integer` | `false` | Stock item ID e.g. `20000`      |
| `data[].is_assembled`              | `boolean` | `false` | `true` if object is assembled      |
| `data[].released_by`               | `string`  | `false` | The user who released/assembled the item e.g. `Name 12`    |
| `data[].scheduled_for_release_at`  | `date`    | `false` | Scheduled date for release/assembly e.g. `2021-10-10` |
| `data[].released_for_shipment_at`  | `date`    | `false` | Date of release/assembly e.g. `2021-10-11` |
| `data[].claimed_by_dealer_id`      | `integer` | `false` | Dealer-id who claimed the stock item `5393`       |
| `data[].outbound_order_id`         | `integer` | `false` | The Outbound Order ID e.g. `20001`      |
| `data[].outbound_order_item_id`    | `integer` | `false` | The Outbound Order Item ID e.g. `20002`      |
| `data[].outbound_shipment_id`      | `integer` | `false` | The Outbound Shipment ID e.g. `20003`      |
| `data[].outbound_shipment_item_id` | `integer` | `false` | The Outbound Shipment Item ID e.g. `20004`      |
| `data[].is_sold_to_customer`       | `boolean` | `false` | Boolean whether the item is sold      |
| `pagination.next_offset`           | `integer`    | `true`  | If not null use in next paginated request in `offset` GET parameter                          |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/warehouse/workshop/assemblies.json?start_date=:start_date&end_date=:end_date</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/warehouse/workshop/assemblies.json?start_date=:start_date&end_date=:end_date&offset=:offset</h6>
	</div>
</div>


> Response

```json
{
  "error": false,
  "error_message": null,
  "data": [
    {
      "stock_item_id": 10000,
      "is_assembled": true,
      "released_by": "Name 11",
      "scheduled_for_release_at": "2021-10-10",
      "released_for_shipment_at": "2021-10-11",
      "claimed_by_dealer_id": 5393,
      "outbound_order_id": 10001,
      "outbound_order_item_id": 10002,
      "outbound_shipment_id": 10003,
      "outbound_shipment_item_id": 10004,
      "is_sold_to_customer": true
    },
    {
      "stock_item_id": 20000,
      "is_assembled": false,
      "released_by": "Name 12",
      "scheduled_for_release_at": "2021-10-10",
      "released_for_shipment_at": "2021-10-11",
      "claimed_by_dealer_id": 5393,
      "outbound_order_id": 20001,
      "outbound_order_item_id": 20002,
      "outbound_shipment_id": 20003,
      "outbound_shipment_item_id": 20004,
      "is_sold_to_customer": false
    }
  ],
  "pagination": {
    "next_offset": null
  }
}
```
