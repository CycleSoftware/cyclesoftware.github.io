# Introduction #

Welcome to the CycleSoftware API documentation

**Documentation overview**

- [CycleSoftware API docs](index.html)
- [Warehouse API docs](warehouse.html)
- [Supplier integration API docs](supplier.html)
- [Stock platform API docs](platform.html)
- [TWSC API docs](https://github.com/CycleSoftware/oauth2-twsc/)

## API endpoints ##

Use the API endpoint hosts according to the country of your account;

| Country code | API endpoint host      |
|--------------|------------------------|
| `NL`         | `api.cyclesoftware.nl` |
| `BE`         | `api.cyclesoftware.be` |
| `FR`         | `api.cyclesoftware.fr` |
| `other`      | `api.cyclesoftware.nl` |

## Requirements ##

To use the APIs you'll need API credentials. The API credentials are provided by CS or available in your account.

* You should access the API over HTTPS
* Where possible use Accept-encoding: gzip. For data api's this might be required.

<aside class="notice">
  Contact <a href="mailto:support@cyclesoftware.nl">support</a> for more information about the API credentials
</aside>

## Request/Response Format ##

The APIs consist of SOAP/WSDL webservices and JSON endpoints.

The default response format is JSON. Requests with a message-body use plain JSON to set or update resource attributes.
Successful requests will return a `200 OK` HTTP status.

## Errors ##

Occasionally you might encounter errors when accessing the REST API. There are four possible types:

| Error Code                  | Error Type                                                              |
|-----------------------------|-------------------------------------------------------------------------|
| `400 Bad Request`           | Invalid request, e.g. using an unsupported HTTP method, or GET variable |
| `401 Unauthorized`          | Authentication or permission error, e.g. incorrect credentials          |
| `403 Forbidden`             | Authentication or permission error                                      |
| `404 Not Found`             | Requests to resources that don't exist or are missing                   |
| `429 Too Many Requests`     | API limit reached, see api limiting                                     |
| `500 Internal Server Error` | Server error                                                            |

> JSON error response

```json
{
  "error": true,
  "error_message": "Unauthorized"
}
```

> XML error response

```xml
<?xml version="1.0"?>
<result>
  <error>1</error>
  <error_message>Unauthorized</error_message>
</result>
```

> SOAP error response

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Body>
    <SOAP-ENV:Fault>
      <faultcode>400</faultcode>
      <faultstring>The problem description</faultstring>
    </SOAP-ENV:Fault>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Errors return both an appropriate HTTP status code and response object which contains a `error`, and `error_message`

## API Parameters ##

Almost all endpoints accept optional parameters which can be passed as an HTTP query string parameter,
e.g. `GET /v1/endpoint?status=completed`. All parameters are documented along each endpoint.

## API Pagination ##

For certain endpoints pagination is implemented. The mechanism differs per endpoint. But the default pagination
mechanism is as follows:

> JSON response

```json
{
  "error": false,
  "error_message": null,
  "data": [],
  "pagination": {
    "next_offset": 1000
  }
}
```

`GET /v1/endpoint?offset=1000`

In the response the next_offset is suggested. You can pass the next offset in the `offset` GET parameter.

## API Types ##

Some general information about responses:

* Amounts could be specified in cents (which will be clear by the fieldname) or with decimal-strings

| Scope       | Description                                            | Example                                |
|-------------|--------------------------------------------------------|----------------------------------------|
| `string`    | An UTF-8 string of variadic length                     | `Hello world!`                         |
| `boolean`   | Boolean `true` or `false`                              | `true`                                 |
| `integer`   | 64-bit signed integer                                  | `1212`                                 |
| `decimal`   | Decimal number with 2 decimals e.g. `0.22`             | `0.22`                                 |
| `float`     | A floating-point number with `.` used as the separator | `123.22`                               |
| `date`      | Date in `yyyy-mm-dd` format                            | `2023-01-23`                           |
| `datetime`  | Datetime in `yyyy-mm-dd hh:mm:ss` format               | `2023-01-23 12:34:33`                  |
| `timestamp` | UNIX timestamp (seconds since Unix Epoch)              | `1678348370`                           |
| `uuid`      | UUID string                                            | `20c5d026-68b3-11ec-90d6-0242ac120003` |
| `array`     | List of sub types                                      | `[10,22]`                              |
| `object`    | An object                                              | `{"field": 1}`                         |

<aside class="notice">
Some fields may also contain a null value, which is annotated with the ? prefix.

For example, `?datetime` means that the following field may contain a valid `datetime` value, a `null`, or may not be
present in the request/response at all.
</aside>

<aside class="notice">
Additionally, some fields may be arrays, which is annotated with the `[]` suffix.

For example, `integer[]` represents an integer array.
</aside>


<aside class="notice">
Fields containing a monetary amount are usually specified in cents (which will be clear by the fieldname) or with decimal-strings. 
</aside>

## API Limits ##

Since may 2022 api-limits are introduced. For endpoints that implement limits the following HTTP response headers are
available.

If the limit is reached, the server will respond with an `HTTP 429 - Too Many Requests` error.

The following HTTP headers are present in an limited endpoint response

| HTTP Response header             | Description                                                                         |
|----------------------------------|-------------------------------------------------------------------------------------|
| `X-RateLimit-Minutely-Limit`     | Contains the number of allowed requests per minute                                  |
| `X-RateLimit-Minutely-Remaining` | Contains the number of remaining requests available within moving minutely interval |
| `X-RateLimit-Daily-Limit`        | Contains the number of daily allowed requests                                       |
| `X-RateLimit-Daily-Remaining`    | Contains the number of daily remaining requests                                     |
| `X-RateLimit-Daily-Reset`        | Contains the UNIX timestamp when the daily limit is reset                           |

## API Scopes ##

| Scope          | Description                                                                           |
|----------------|---------------------------------------------------------------------------------------|
| `common`       | Access common data such as employees, enums, suppliers                                |
| `e-commerce`   | Access e-commerce related endpoints (stock, order-creation, articledata)              |
| `resources`    | Access object resources such as `customers`, `workshop-orders`, `repair-objects` etc. |
| `stock-export` | Bulk export stock data                                                                |
| `sales-export` | Bulk export sales data                                                                |
| `rental`       | Rental related information                                                            |
| `warehouse`    | Warehouse related data                                                                |
| `platform`     | Access authorized dealer-data for sales-platforms                                     |
