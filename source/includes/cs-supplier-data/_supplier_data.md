# Supplier data #

The supplier data APIs are designed for pulling article-information for a specific supplier

***Authentication***

- Basic HTTP Authentication
- Scope(s): `e-commerce`, `articledata`

## Supplier data - V4 ##

Get supplier data available for a specific `supplier_id`.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v4/supplierdata/:supplier_id.json</h6>
	</div>
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v4/supplierdata/:supplier_id.json?token=:token</h6>
	</div>
</div>

| URL parameter  | Type      | Description                                                                                                                                               |
|----------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `:supplier_id` | `integer` | The supplier ID, see <a href="https://docs.cyclesoftware.nl/#common-supplier-list">common suppliers endpoint</a> <i class="label label-info">required</i> |


| GET parameter        | Type      | Description                                                                       |
|----------------------|-----------|-----------------------------------------------------------------------------------|
| `:modified_since`    | `integer` | Only return entries with modification after this value                            |
| `:exclude_articles`  | `boolean` | If `true` exclude articles (defaults to `false`)                                  |
| `:exclude_objects`   | `boolean` | If `true` exclude objects / bicycles (defaults to `false`)                        |

### Response properties ###

For documentation of properties see <a href="https://docs.cyclesoftware.nl/#article-data-articledata-v4">article data endpoint</a>

The `data[].stock` and `data[].objects` are not available in the response for this endpoint.
