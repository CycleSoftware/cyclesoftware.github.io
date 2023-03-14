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

| GET parameter            | Type      | Description                                                                                                                                                |
|--------------------------|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `payment_amount_cents`   | `integer` | The payment amount in cents. Only applicable for advance order payments endpoint                                                                           |
| `dynamic_payment_amount` | `bool`    | `true` if the amount in the payment link should depend dynamically on unpayed amount of the order. If a `payment_amount_cents` this option will be ignored |

| Property                         | Type       | Description                                                                                         |
|----------------------------------|------------|-----------------------------------------------------------------------------------------------------|
| `error`                          | `boolean`  | `true` if an error occurred                                                                         |
| `error_message`                  | `?string`  | The error message if an error occurred                                                              |
| `data.sales_order_id`            | `?integer` | The sales order ID `1000`                                                                           |
| `data.sales_transaction_number`  | `?integer` | The sales transaction number (invoice number)                                                       |
| `data.payment_url`               | `string`   | Payment portal URL `https://twsc.nl/p/xM4iatg`                                                      |
| `data.total_amount_cents`        | `integer`  | Total amount in cents of the order or invoice `100000`                                              |
| `data.already_payed_cents`       | `integer`  | The amount already payed in cents e.g. `50000`                                                      |
| `data.payment_link_amount_cents` | `integer`  | The payment amount in the portal e.g. `25000`                                                       |
| `data.dynamic_payment_amount`    | `bool`     | `true` if the amount to be payed is dynamic and depends on unpayed amount of the order or invoice   |
| `data.qr_code`                   | `string`   | The QR code of the payment portal url as data uri `data:image/png;base64,iVBORw0KGgoAAAANSUhEU....` |

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
Content-length: 425
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

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
        "dynamic_payment_amount": false,
        "qr_code": "data:image/png;base64,iVBORw0KGgoAAAANSUhEU...."
    }
}
```

