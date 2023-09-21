# Vouchers #

Read vouchers

***Scope(s)***

- `resources`

## Voucher (object)

| **Property**                | **Type**  | **Description**                                                   |
|-----------------------------|-----------|-------------------------------------------------------------------|
| `error`                     | `boolean` | `true` if an error occurred.                                      |
| `error_message`             | `?string` | Error message if occurred.                                        |
| `data.code`                 | `string`  | Voucher code e.g. `5455-7407-8042-8985`                           |
| `data.type_id`              | `integer` | Voucher type ID e.g. `1` (see `voucher_types` in common enum API) |
| `data.type_description`     | `string`  | Voucher type description `Waardebon`                              |
| `data.is_active`            | `boolean` | `false` if the voucher is not useable                             |
| `data.amount_initial_cents` | `integer` | The amount in cents when the voucher was issued `2000`            |
| `data.amount_spent_cents`   | `integer` | The amount in cents spent for the voucher `1500`                  |
| `data.amount_balance_cents` | `integer` | The amount which can be used in cents e.g. `500`                  |

## Voucher info

Get voucher by code

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v1/vouchers/:code.json</h6>
    </div>
</div>

| **URI parameter** | **Type** | **Description**                                |
|-------------------|----------|------------------------------------------------|
| `code`            | `string` | The voucher code ID e.g. `1000-2000-3000-4000` |

> HTTP request

```http
GET /api/v1/vouchers/1000-2000-3000-4000.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
Content-length: 309
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
    "error": false,
    "error_message": null,
    "data": {
        "code": "1000-2000-3000-4000",
        "type_id": 1,
        "type_description": "Waardebon",
        "is_active": true,
        "amount_initial_cents": 2000,
        "amount_spent_cents": 1500,
        "amount_balance_cents": 500
    }
}
```
