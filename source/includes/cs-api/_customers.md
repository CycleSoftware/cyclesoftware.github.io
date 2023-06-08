# Customers #

Find, create and update customers

***Scope(s)***

- `resources`

## Customer (object)

| Property                          | Type        | Modify                     | Description                                                   |
|-----------------------------------|-------------|----------------------------|---------------------------------------------------------------|
| `customer_id`                     | `integer`   | `readonly`                 | Customer ID e.g. `6`                                          |
| `customer_type_name`              | `string`    | <code>PUT&#124;POST</code> | See common enum `customer_types` e.g. `Klant`                 |
| `customer_reference`              | `string`    | <code>PUT&#124;POST</code> | Reference of customer e.g. `OwnRef`                           |
| `postcode`                        | `string`    | <code>PUT&#124;POST</code> | Postcode of customer e.g. `5488HM`                            |
| `house_number`                    | `string`    | <code>PUT&#124;POST</code> | House number of customer e.g. `1`                             |
| `house_number_postfix`            | `string`    | <code>PUT&#124;POST</code> | House number postfix of customer e.g. `c`                     |
| `attn`                            | `string`    | <code>PUT&#124;POST</code> | Attn name `Name of address`                                   |
| `title`                           | `string`    | <code>PUT&#124;POST</code> | Name prefix e.g. `Dhr./Mevr. `                                |
| `initials`                        | `string`    | <code>PUT&#124;POST</code> | Initials e.g. `T`                                             |
| `insertion`                       | `string`    | <code>PUT&#124;POST</code> | Insertion e.g. `van`                                          |
| `first_name`                      | `string`    | <code>PUT&#124;POST</code> | First name e.g. `Tim`                                         |
| `name`                            | `string`    | <code>PUT&#124;POST</code> | Last name e.g. `LastName`                                     |
| `street`                          | `string`    | <code>PUT&#124;POST</code> | Street e.g. `Raadhuisplein`                                   |
| `city`                            | `string`    | <code>PUT&#124;POST</code> | City e.g. `Nistelrode`                                        |
| `country_code_iso_3166`           | `string`    | <code>PUT&#124;POST</code> | Country code e.g. `NL`                                        |
| `email`                           | `string`    | <code>PUT&#124;POST</code> | E-mail e.g. `name@domain.nl`                                  |
| `discount_percentage`             | `decimal`   | <code>PUT&#124;POST</code> | Default discount percentage e.g. `10`                         |
| `datetime_created`                | `?datetime` | `readonly`                 | Created at if available e.g. `2023-01-03 12:30:44`            |
| `phone_numbers`                   | `object[]`  | <code>PUT&#124;POST</code> | array of phone numbers                                        |
| `phone_numbers[].phone_number_id` | `string`    | <code>PUT&#124;POST</code> | ID of phone number e.g. `tel` (landline) `mob` (mobile) or ID |
| `phone_numbers[].customer_id`     | `integer`   | `readonly`                 | Customer ID e.g. `6`                                          |
| `phone_numbers[].phone_number`    | `string`    | <code>PUT&#124;POST</code> | Phone number e.g. `0733030050`                                |
| `phone_numbers[].name`            | `string`    | <code>PUT&#124;POST</code> | Name of number e.g. `Dhr./Mevr.  T UnitTest`                  |


## Get Customer 

Get customer

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v1/customers/:customer_id.json</h6>
    </div>
</div>

| **URI parameter** | **Type** | **Description**         |
|-------------------|----------|-------------------------|
| `customer_id`     | `int`    | Customer ID e.g. `1006` |

The result will be a [Customer (object)](#customers-customer-object)

> HTTP request

```http
GET /api/v1/customers/1006.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000
Content-length: 914

{
    "customer_id": 1006,
    "customer_type_name": "Klant",
    "customer_reference": "OwnRef",
    "postcode": "5388GM",
    "house_number": "1",
    "house_number_postfix": "c",
    "attn": "Name of address",
    "title": "Dhr./Mevr. ",
    "initials": "T",
    "insertion": "van",
    "first_name": "Tim",
    "name": "LastName",
    "street": "Raadhuisplein",
    "city": "Nistelrode",
    "country_code_iso_3166": "NL",
    "email": "name@domain.nl",
    "discount_percentage": 0,
    "datetime_created": "2023-01-03 12:30:44",
    "phone_numbers": [
        {
            "phone_number_id": "mob",
            "customer_id": 6,
            "phone_number": "06-12345678",
            "name": "Dhr./Mevr. T UnitTest"
        },
        {
            "phone_number_id": "tel",
            "customer_id": 6,
            "phone_number": "0733030050",
            "name": "Dhr./Mevr.  T UnitTest"
        }
    ]
}
```

## Create customer

Create a customer

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">POST</i>
        <h6>/api/v1/customers.json</h6>
    </div>
</div>


> HTTP request

```http
POST /api/v1/customers.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8
Content-length: 1030

{
    "customer_type_name": "Zakelijk",
    "customer_reference": "",
    "postcode": "18000",
    "house_number": "1",
    "house_number_postfix": "2",
    "attn": "attn",
    "title": "M",
    "initials": "A",
    "insertion": "S",
    "first_name": "Adri",
    "name": "Aleksnadar",
    "street": "street",
    "city": "city",
    "country_code_iso_3166": "sr",
    "email": "email@mail.com",
    "discount_percentage": 10,
    "datetime_created": null,
    "phone_numbers": [
        {
            "phone_number_id": "mob",
            "customer_id": 26196,
            "phone_number": "+381 60 2222222",
            "name": "Adri S Aleksnadar"
        },
        {
            "phone_number_id": "tel",
            "customer_id": 26196,
            "phone_number": "",
            "name": "Adri S Aleksnadar"
        },
        {
            "phone_number_id": "714253",
            "customer_id": 26196,
            "phone_number": "+381 60 3333333",
            "name": "Extra 1"
        }
    ]
}
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000
Content-length: 1030

{
    "customer_id": 26196,
    "customer_type_name": "Zakelijk",
    "customer_reference": "",
    "postcode": "18000",
    "house_number": "1",
    "house_number_postfix": "2",
    "attn": "attn",
    "title": "M",
    "initials": "A",
    "insertion": "S",
    "first_name": "Adri",
    "name": "Aleksnadar",
    "street": "street",
    "city": "city",
    "country_code_iso_3166": "sr",
    "email": "email@mail.com",
    "discount_percentage": 10,
    "datetime_created": null,
    "phone_numbers": [
        {
            "phone_number_id": "mob",
            "customer_id": 26196,
            "phone_number": "+381 60 2222222",
            "name": "Adri S Aleksnadar"
        },
        {
            "phone_number_id": "tel",
            "customer_id": 26196,
            "phone_number": "",
            "name": "Adri S Aleksnadar"
        },
        {
            "phone_number_id": "714253",
            "customer_id": 26196,
            "phone_number": "+381 60 3333333",
            "name": "Extra 1"
        }
    ]
}
```

## Update customer

Update a customer

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">PUT</i>
        <h6>/api/v1/customers/:customer_id.json</h6>
    </div>
</div>

| **URI parameter** | **Type** | **Description**      |
|-------------------|----------|----------------------|
| `customer_id`     | `int`    | Customer ID e.g. `4` |


> HTTP request

```http
PUT /api/v1/customers/4.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic
Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8
Content-length: 873

{
    "customer_id": 4,
    "customer_type_name": "Klant",
    "customer_reference": "",
    "postcode": "5243RB",
    "house_number": "38",
    "house_number_postfix": "",
    "attn": "",
    "title": "Dhr./Mevr. ",
    "initials": "G",
    "insertion": "",
    "first_name": "",
    "name": "Name 64070233d1b8c",
    "street": "Bruggen",
    "city": "Rosmalen",
    "country_code_iso_3166": "NL",
    "email": "test@hotmail.com",
    "discount_percentage": 0,
    "datetime_created": null,
    "phone_numbers": [
        {
            "phone_number_id": "mob",
            "customer_id": 4,
            "phone_number": "",
            "name": "Dhr./Mevr.  G Name 64070233d1b8c"
        },
        {
            "phone_number_id": "tel",
            "customer_id": 4,
            "phone_number": "",
            "name": "Dhr./Mevr.  G Name 64070233d1b8c"
        }
    ]
}
```

> HTTP Response

```http
HTTP/1.1 200
Content-type: application/json; charset=utf-8
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000
Content-length: 873

{
    "customer_id": 4,
    "customer_type_name": "Klant",
    "customer_reference": "",
    "postcode": "5243RB",
    "house_number": "38",
    "house_number_postfix": "",
    "attn": "",
    "title": "Dhr./Mevr. ",
    "initials": "G",
    "insertion": "",
    "first_name": "",
    "name": "Name 64070233d1b8c",
    "street": "Bruggen",
    "city": "Rosmalen",
    "country_code_iso_3166": "NL",
    "email": "test@hotmail.com",
    "discount_percentage": 0,
    "datetime_created": null,
    "phone_numbers": [
        {
            "phone_number_id": "mob",
            "customer_id": 4,
            "phone_number": "",
            "name": "Dhr./Mevr.  G Name 64070233d1b8c"
        },
        {
            "phone_number_id": "tel",
            "customer_id": 4,
            "phone_number": "",
            "name": "Dhr./Mevr.  G Name 64070233d1b8c"
        }
    ]
}
```



## Find customers

Find existing customers

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">GET</i>
        <h6>/api/v1/customers/find.json?phone_number=:phone_number&..</h6>
    </div>
</div>

| **GET parameter**     | **Type**  | **Description**                             |
|-----------------------|-----------|---------------------------------------------|
| `phone_number`        | `?string` | Phone number of customer e.g. `0733030050`  |
| `postal_code`         | `?string` | Postal code of customer e.g. `5388GM`       | 
| `housenumber`         | `?string` | Housenumber of customer e.g. `1`            | 
| `housenumber_postfix` | `?string` | Housenumber_postfix of customer e.g. `a`    | 
| `email`               | `?string` | E-mail of customer e.g. `name@domain.nl`    | 
| `query`               | `?string` | Query to search for e.g. `name of customer` | 
| `country_code`        | `?string` | Country code of customer e.g. `NL`          | 

The result will be an array of [Customer (object)](#customers-customer-object)

> HTTP request

```http
GET /api/v1/customers/find.json?phone_number=0733030050 HTTP/1.1
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
Content-length: 44656
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000

[
    {
        "customer_id": 8,
        "customer_type_name": "Klant",
        "customer_reference": "REF46",
        "postcode": "8448PE",
        "house_number": "32",
        "house_number_postfix": "B",
        "attn": "",
        "title": "Dhr.",
        "initials": "A",
        "insertion": "Van",
        "first_name": "Adri",
        "name": "Name 235238848",
        "street": "Mauritslaan",
        "city": "Heerenveen",
        "country_code_iso_3166": "NL",
        "email": "test235238848@cyclesoftware.nl",
        "discount_percentage": 0,
        "datetime_created": null,
        "phone_numbers": [
            {
                "phone_number_id": "mob",
                "customer_id": 8,
                "phone_number": "0733030050",
                "name": "Adri Van Name 235238848"
            },
            {
                "phone_number_id": "tel",
                "customer_id": 8,
                "phone_number": "",
                "name": "Adri Van Name 235238848"
            },
            {
                "phone_number_id": "453383",
                "customer_id": 8,
                "phone_number": "06 24238848",
                "name": "Extra 1"
            }
        ]
    },
    {
        "customer_id": 11,
        "customer_type_name": "E-commerce",
        "customer_reference": "REFBE1",
        "postcode": "1000",
        "house_number": "2",
        "house_number_postfix": "B",
        "attn": "",
        "title": "Dhr.",
        "initials": "G",
        "insertion": "van",
        "first_name": "Giel",
        "name": "Wijgergangs",
        "street": "Belgische weg",
        "city": "Belgcity",
        "country_code_iso_3166": "BE",
        "email": "gielwijgergangs@gmail.com",
        "discount_percentage": 0,
        "datetime_created": null,
        "phone_numbers": [
            {
                "phone_number_id": "mob",
                "customer_id": 11,
                "phone_number": "06 22903913",
                "name": "Giel van Wijgergangs"
            },
            {
                "phone_number_id": "tel",
                "customer_id": 11,
                "phone_number": "073 303 0050",
                "name": "Giel van Wijgergangs"
            }
        ]
    }
]
```

