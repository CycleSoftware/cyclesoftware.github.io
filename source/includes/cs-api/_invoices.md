# Invoices #

Access invoice data

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `salesdata`

## Unbooked invoices ##

Get a list of unbooked sales transactions / invoices.

| GET parameter               | Type      | Description                                                                                                          |
|-------------------------|-----------|----------------------------------------------------------------------------------------------------------------------|
|`offset`                  | integer    | Pagination offset. <i class="label label-info">optional</i>                                                                                                          |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/invoices/unbooked.json</h6>
	</div>
</div>

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/invoices/unbooked.json?offset=1000</h6>
	</div>
</div>

> Response
```json
{}
```
