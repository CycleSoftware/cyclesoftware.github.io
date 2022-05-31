# Outbound orders #

Outbound orders related APIs

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `warehouse`

## Convert pool to regular ##

Convert a POOL order to a regular order.

| URL parameter        | Type      | Description                                                |
|----------------------|-----------|------------------------------------------------------------|
| `:outbound_order_id` | `integer` | Outbound order id <i class="label label-info">required</i> |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/warehouse/outbound/order/:outbound_order_id/pool-to-regular.json</h6>
	</div>
</div>


> HTTP Request 

```http
POST /api/v1/warehouse/outbound/order/1013123/pool-to-regular.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip,deflate
Accept: application/json
Content-type: application/json; charset=utf-8
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 722

{
  "error": false,
  "error_message": null
}
```
