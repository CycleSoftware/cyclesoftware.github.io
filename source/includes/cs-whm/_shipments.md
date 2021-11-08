# Shipments #

Access outbound shipment data

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `warehouse`

## Delivery status for object item id ##

Mark the shipment for a stock item as `delivered` or `not-delivered`. `not-delivered` should be used if the package could not be delivered at the destination.

| URL parameter               | Type      | Description                                                                                                          |
|-------------------------|-----------|----------------------------------------------------------------------------------------------------------------------|
|`:stock_item_id`                  | `integer`    | Stock item ID in warehouse <i class="label label-info">required</i>                                                                                                         |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/warehouse/outbound/item/:stock_item_id/delivered.json</h6>
	</div>
</div>


<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/warehouse/outbound/item/:stock_item_id/not-delivered.json</h6>
	</div>
</div>

> Response

```json
{
  "error": false,
  "error_message": null
}
```
