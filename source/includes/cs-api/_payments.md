# Payments #

Access payment portal links

***Authentication mechanism***

- Basic HTTP Authentication
- Scopes: `e-commerce`

## Payment links ##

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/payments/order/:id/payment-link.json</h6>
	</div>
</div>
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/payments/invoice/:id/payment-link.json</h6>
	</div>
</div>

| URI parameter | Type      | Description                                              |
|---------------|-----------|----------------------------------------------------------|
| `id`          | `integer` | Sales order ID or the invoice / sales transaction number |

| GET parameter          | Type      | Description                                                                      |
|------------------------|-----------|----------------------------------------------------------------------------------|
| `payment_amount_cents` | `integer` | The payment amount in cents. Only applicable for advance order payments endpoint |

| Property                         | Type      | Nullable | Description                                                                                         |
|----------------------------------|-----------|----------|-----------------------------------------------------------------------------------------------------|
| `error`                          | `boolean` | `false`  | `true` if an error occurred                                                                         |
| `error_message`                  | `string`  | `true`   | The error message if an error occurred                                                              |
| `data.sales_order_id`            | `integer` | `true`   | The sales order ID `1000`                                                                           |
| `data.sales_transaction_number`  | `integer` | `true`   | The sales transaction number (invoice number)                                                       |
| `data.payment_url`               | `string`  | `false`  | Payment portal URL `https://twsc.%s/p/xM4iatg`                                                      |
| `data.total_amount_cents`        | `integer` | `false`  | Total amount in cents of the order or invoice `100000`                                              |
| `data.already_payed_cents`       | `integer` | `false`  | The amount already payed in cents e.g. `50000`                                                      |
| `data.payment_link_amount_cents` | `integer` | `false`  | The payment amount in the portal e.g. `25000`                                                       |
| `data.qr_code`                   | `string`  | `false`  | The QR code of the payment portal url as data uri `data:image/png;base64,iVBORw0KGgoAAAANSUhEU....` |

> HTTP request

```http
GET /api/v1/payments/order/1012/payment-link.json?payment_amount_cents=10000 HTTP/1.1
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
    "error": false,
    "error_message": null,
    "data": {
        "sales_order_id": 1012,
        "sales_transaction_number": null,
        "payment_url": "https://twsc.nl/p/xM4iatg",
        "total_amount_cents": 250000,
        "already_payed_cents": 10000,
        "payment_link_amount_cents": 10000,
        "qr_code": "data:image/png;base64,iVBORw0KGgoAAAANSUhEU...."
    }
}
```

