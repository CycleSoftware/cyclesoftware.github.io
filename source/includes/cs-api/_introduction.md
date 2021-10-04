# Introduction #

Welcome to the CycleSoftware API documentation

| API type | Documentation             |
|-------------|---------------------------|
| `CS api` | [CycleSoftware API docs](index.html) |
| `Warehouse api` | [Warehouse API docs](warehouse.html) |
| `TWSC api` | [TWSC API docs](https://github.com/CycleSoftware/oauth2-twsc/) |

## API endpoint ##

Use the following domain: `https://api.cyclesoftware.nl/` unless otherwise specified.

## Requirements ##

To use the APIs you'll need API credentials. The API credentials are provided by CS or available in your account.

* You should access the API over HTTPS
* Where possible use Accept-encoding: gzip. For data api's this might be required.

<aside class="notice">
  You can contact <a href="mailto:support@cycleesoftware.nl">support</a> for more information about the API credentials
</aside>

## Request/Response Format ##

The APIs consist of SOAP/WSDL webservices and JSON endpoints.

The default response format is JSON. Requests with a message-body use plain JSON to set or update resource attributes.
Successful requests will return a `200 OK` HTTP status.

Some general information about responses:

* Datetimes are returned in format (unless specified otherwise): `YYYY-MM-DD HH:MM:SS`
* Dates are returned in format (unless specified otherwise): `YYYY-MM-DD`
* Amounts could be specified in cents (which will be clear by the fieldname) or with decimal-strings

## Errors ##

Occasionally you might encounter errors when accessing the REST API. There are four possible types:

| Error Code                  | Error Type                                                  |
|-----------------------------|-------------------------------------------------------------|
| `400 Bad Request`           | Invalid request, e.g. using an unsupported HTTP method, or GET variable     |
| `401 Unauthorized`          | Authentication or permission error, e.g. incorrect credentials |
| `403 Forbidden`          | Authentication or permission error |
| `404 Not Found`             | Requests to resources that don't exist or are missing       |
| `500 Internal Server Error` | Server error                                                |

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

## Parameters ##

Almost all endpoints accept optional parameters which can be passed as a HTTP query string parameter,
e.g. `GET /v1/endpoint?status=completed`. All parameters are documented along each endpoint.

## Pagination ##

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

In the response the next_offset is suggested. You can pass the next offset in the `offset` GET paramater.

## Libraries and Tools ##

### Official libraries ###

- [PHP TWSC api](https://packagist.org/packages/cyclesoftware/oauth2-twsc)
