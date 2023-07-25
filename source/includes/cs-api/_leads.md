# Leads #

Create, read and cancel sales leads

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `resources`

## Properties ##

| **Field**                                            | **Type**   | **Description**                                                                                                 | **Example value**                            |
|------------------------------------------------------|------------|-----------------------------------------------------------------------------------------------------------------|----------------------------------------------|
| `error`                                              | `boolean`  | true if an error occurred                                                                                       | false                                        |
| `error_message`                                      | `?string`  | Empty if no error                                                                                               |                                                  
| `sales_lead.uuid`                                    | `string`   | Unique identifier of the lead (null on creation)                                                                | 0c6b40a4-a217-11e8-92bb-005056a46320         |
| `sales_lead.store_id`                                | `string`   | The store identification format of \[account\]-\[store\]                                                        | 1000-2                                       |
| `sales_lead.type`                                    | `string`   | Type of the lead (see type list)                                                                                | information                                  |
| `sales_lead.status`                                  | `string`   | Status of the lead (see status list)                                                                            | open                                         |
| `sales_lead.title`                                   | `string`   | Short title of lead description                                                                                 | Kieskeurig: proefrit Batavus Crescendo       |
| `sales_lead.message`                                 | `string`   | Message to the dealer about the lead                                                                            | Een potientiele klant wil een proefrit maken |
| `sales_lead.costs_ex_vat_cents`                      | `integer`  | The costs that the platform charges to the dealer on acceptance of the lead, not relevant for `resources` scope | 1500                                         |
| `sales_lead.options.test_ride_requested`             | `boolean`  | provide true if a test-ride is requested                                                                        | false                                        |
| `sales_lead.options.phone_call_requested`            | `boolean`  | provide true if the dealer should call the customer                                                             | false                                        |
| `sales_lead.options.finance_information_requested`   | `boolean`  | provide true if the dealer should provide financial information                                                 | false                                        |
| `sales_lead.options.insurance_information_requested` | `boolean`  | provide true if the dealer should provide insurance information                                                 | false                                        |
| `sales_lead.object.description`                      | `string`   | Description of the object                                                                                       | Batavus Crescendo                            |
| `sales_lead.object.object_id`                        | `integer`  | Object id in stock dealer (can be retrieved in stock locator api)                                               | 12212                                        |
| `sales_lead.object.article_number`                   | `string`   | Article number of the object                                                                                    | ART1                                         |
| `sales_lead.object.barcode`                          | `string`   | EAN barcode of the object                                                                                       | 877474749349                                 |
| `sales_lead.exchange_object.exchange_description`    | `string`   | Description of the exchange object                                                                              |                                              |
| `sales_lead.exchange_object.exchange_remarks`        | `string`   | Remarks about the exchange object                                                                               |                                              |
| `sales_lead.customer.customer_address_id`            | `?integer` | ID of the customer address (null on creation)                                                                   | 91953                                        |
| `sales_lead.customer.address_type`                   | `string`   | lead  null on creation                                                                                          | lead                                         |
| `sales_lead.customer.customer_id`                    | `integer`  | Customer ID if address is linked to a customer null on creation)                                                | 235240102                                    |
| `sales_lead.customer.is_business_address`            | `boolean`  | true if address is for a company                                                                                | false                                        |
| `sales_lead.customer.company_name`                   | `string`   | The company name                                                                                                |                                              |
| `sales_lead.customer.name`                           | `string`   | Name of the customer                                                                                            | Name 91953                                   |
| `sales_lead.customer.street`                         | `string`   | Street of the address                                                                                           | Slangenburg                                  |
| `sales_lead.customer.house_number`                   | `string`   | Housenumber                                                                                                     | 314                                          |
| `sales_lead.customer.house_number_postfix`           | `string`   | Housenumber suffix                                                                                              | B                                            |
| `sales_lead.customer.postal_code`                    | `string`   | Postalcode                                                                                                      | 7423ZR                                       |
| `sales_lead.customer.city`                           | `string`   | City                                                                                                            | Deventer                                     |
| `sales_lead.customer.country_code`                   | `string`   | Country code (ISO 3166)                                                                                         | NL                                           |
| `sales_lead.customer.phone_number`                   | `string`   | Phonenumber                                                                                                     | 06 38668303                                  |
| `sales_lead.customer.email`                          | `string`   | E-mail address                                                                                                  | email91953@example.nl                        |
| `sales_lead.customer.notes`                          | `string`   | Extra information about the customer address                                                                    |
| `sales_lead.created_at`                              | `datetime` | When the lead was created (null on creation)                                                                    | 2020-04-14T06:33:26+02:00                    |
| `sales_lead.modified_at`                             | `datetime` | When the lead was last modified (null on creation)                                                              | 2020-04-14T06:33:26+02:00                    |

## Sales lead types ##

Possible values for `sales_lead.type`

| **Field**         | **Description**                                |
|-------------------|------------------------------------------------|
| `information`     | The customer would like to receive information |
| `sales_offer`     | The customer would like to buy the object      |
| `test_ride`       | The customer would like to make a test-ride    |
| `contact_request` | The customer would like to be contacted        |
| `exchange`        | The customer would like to exchange an object  |
| `complaint`       | The customer has a complaint                   |
| `other`           | -                                              |


## Sales lead status ##

Possible values for `sales_lead.status`

| **Field**   | **Description**                                                  |
|-------------|------------------------------------------------------------------|
| `open`      | The dealer did not take any action on the lead                   |
| `noticed`   | The dealer has noticed the lead but did not accept or decline it |
| `accepted`  | The dealer has accepted the lead                                 |
| `declined`  | The dealer has declined the lead                                 |
| `succeeded` | The dealer has successfully converted the lead                   |
| `failed`    | The dealer has not coverted the lead                             |
| `cancelled` | The lead was cancelled                                           |

## Create lead ##

Get a list of stores

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/leads/create.json</h6>
	</div>
</div>

> HTTP request

```http
POST /api/v1/leads/create.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8

{
    "store_id": "1-1",
    "type": "test_ride",
    "status": "open",
    "title": "Kieskeurig: proefrit Batavus Crescendo",
    "message": "NaamKlant wil een proefrit maken",
    "options": {
        "test_ride_requested": true,
        "phone_call_requested": true,
        "finance_information_requested": false,
        "insurance_information_requested": false
    },
    "object": {
        "description": "Batavus Crescendo",
        "object_id": 11212,
        "article_number": null,
        "barcode": "877474749349"
    },
    "exchange_object": {
        "exchange_description": null,
        "exchange_remarks": null
    },
    "customer": {
        "customer_address_id": null,
        "address_type": "lead",
        "customer_id": null,
        "is_business_address": false,
        "company_name": "",
        "name": "NaamKlant",
        "street": "Hoofdstraat",
        "house_number": "10",
        "house_number_postfix": "B",
        "postal_code": "5238HL",
        "city": "Berlicum",
        "country_code": "NL",
        "phone_number": "0612345678",
        "email": "voorbeeld@host.nl",
        "notes": "Bellen tussen 12.00-17.00"
    }
}
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 1357

{
  "error": false,
  "error_message": null,
  "sales_lead": {
    "uuid": "0c6b40a4-a217-11e8-92bb-005056a46320",
    "store_id": "1-1",
    "type": "information",
    "status": "open",
    "title": "Kieskeurig: proefrit",
    "message": "Een potientiele klant wil een proefrit maken",
    "costs_ex_vat_cents": 0,
    "options": {
      "test_ride_requested": false,
      "phone_call_requested": false,
      "finance_information_requested": false,
      "insurance_information_requested": false
    },
    "object": {
      "description": "Batavus Crescendo",
      "object_id": 12212,
      "article_number": "ART1",
      "barcode": "877474749349"
    },
    "exchange_object": {
      "exchange_description": "",
      "exchange_remarks": ""
    },
    "customer": {
      "customer_address_id": 91953,
      "address_type": "delivery_address",
      "customer_id": 235240102,
      "is_business_address": false,
      "company_name": "",
      "name": "Name 91953",
      "street": "Slangenburg",
      "house_number": "314",
      "house_number_postfix": "",
      "postal_code": "7423ZR",
      "city": "Deventer",
      "country_code": "NL",
      "phone_number": "06 38668303",
      "email": "email91953@example.nl",
      "notes": ""
    },
    "created_at": "2020-04-14T06:33:26+02:00",
    "modified_at": "2020-04-14T06:33:26+02:00"
  }
}
```

## Get lead ##

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/leads/:uuid.json</h6>
	</div>
</div>


| URI parameter | Type   | Description                                                      |
|---------------|--------|------------------------------------------------------------------|
| `uuid`        | `uuid` | The UUID of the lead e.g. `0c6b40a4-a217-11e8-92bb-005056a46320` |


> HTTP request

```http
GET /api/v1/leads/0c6b40a4-a217-11e8-92bb-005056a46320.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8
Content-length: 65

```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 1357

{
  "error": false,
  "error_message": null,
  "sales_lead": {
    "uuid": "0c6b40a4-a217-11e8-92bb-005056a46320",
    "store_id": "1-1",
    "type": "information",
    "status": "open",
    "title": "Kieskeurig: proefrit",
    "message": "Een potientiele klant wil een proefrit maken",
    "costs_ex_vat_cents": 0,
    "options": {
      "test_ride_requested": false,
      "phone_call_requested": false,
      "finance_information_requested": false,
      "insurance_information_requested": false
    },
    "object": {
      "description": "Batavus Crescendo",
      "object_id": 12212,
      "article_number": "ART1",
      "barcode": "877474749349"
    },
    "exchange_object": {
      "exchange_description": "",
      "exchange_remarks": ""
    },
    "customer": {
      "customer_address_id": 91953,
      "address_type": "delivery_address",
      "customer_id": 235240102,
      "is_business_address": false,
      "company_name": "",
      "name": "Name 91953",
      "street": "Slangenburg",
      "house_number": "314",
      "house_number_postfix": "",
      "postal_code": "7423ZR",
      "city": "Deventer",
      "country_code": "NL",
      "phone_number": "06 38668303",
      "email": "email91953@example.nl",
      "notes": ""
    },
    "created_at": "2020-04-14T06:33:26+02:00",
    "modified_at": "2020-04-14T06:33:26+02:00"
  }
}
```

## Cancel lead ##

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/leads/:uuid/cancel.json</h6>
	</div>
</div>


| URI parameter | Type   | Description                                                      |
|---------------|--------|------------------------------------------------------------------|
| `uuid`        | `uuid` | The UUID of the lead e.g. `0c6b40a4-a217-11e8-92bb-005056a46320` |


> HTTP request

```http
POST /api/v1/leads/0c6b40a4-a217-11e8-92bb-005056a46320/cancel.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8

```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 45
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

{
  "error": false,
  "error_message": null
}
```
