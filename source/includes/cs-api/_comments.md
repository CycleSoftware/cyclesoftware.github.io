# Comments #

Find, create and update comments

***Scope(s)***

- `resources`, `crm`

## Comment (object)

| Property             | Type        | Modify                     | Description                                                                                      |
|----------------------|-------------|----------------------------|--------------------------------------------------------------------------------------------------|
| `comment_id`         | `integer`   | `readonly`                 | Comment ID e.g. `6`                                                                              |
| `comment_type_id`    | `integer`   | <code>PUT&#124;POST</code> | Comment Type ID e.g. `2`                                                                         |
| `comment_type_name`  | `string`    | `readonly`                 | Comment Type ID description e.g. `Note`, `Warning`                                               |
| `employee_id`        | `integer`   | <code>PUT&#124;POST</code> | Employee ID e.g. `21` (see employees endpoint)                                                   |
| `entity_id`          | `integer`   | <code>POST</code>          | Entity ID e.g. sales order number when `entity_type_id` is 7                                     |
| `entity_type_id`     | `integer`   | <code>POST</code>          | Currently the following entity type id's are allowed (1,3,4,5,6,7) see common API entity_types   |
| `entity_type_name`   | `string`    | `readonly`                 | Entity Type ID description sales order number when `entity_type_id` is 7                         |
| `comment_type_label` | `string`    | `readonly`                 | Comment Type label see common API `comment_types`                                                |
| `customer_id`        | `integer`   | <code>POST</code>          | Customer ID e.g. `1006`                                                                          |
| `comment`            | `string`    | <code>PUT&#124;POST</code> | Comment e.g. `Customer has 10% default discount`                                                 |
| `created_at`         | `?datetime` | `readonly`                 | Created at if available e.g. `2023-01-03 12:30:44`                                               |
| `modified_at`        | `?datetime` | `readonly`                 | Modified at if available e.g. `2023-01-03 12:30:44`                                              |

## Get comment by comment ID

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>/api/v1/comments/:comment_id.json</h6>
    </div>
</div>

| **URI parameter** | **Type**  | **Description**     |
|-------------------|-----------|---------------------| 
| `comment_id`      | `integer` | Comment ID e.g. `6` |

The result will be a [Comments (object)](#comment-object)

> HTTP request

```http
GET /api/v1/comments/227445.json HTTP/1.1
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
Content-length: 637

{
    "error": false,
    "error_message": null,
    "comment": 
        {
            "comment_id": 227445,
            "comment_type_id": 1,
            "comment_type_name": "Note",
            "employee_id": 46933,
            "entity_id": 1006,
            "entity_type_id": 7,
            "entity_type_name": "Order",
            "comment_type_label": "info",
            "customer_id": 1006,
            "created_at": "2020-05-13 09:32:55",
            "modified_at": "2020-05-13 09:32:55",
            "comment": "Default 10% discount"
        }
}
```

## Get comments by entity type ID and entity ID

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>/api/v1/comments/:entity_type_id/:entity_id.json</h6>
    </div>
</div>

| **URI parameter** | **Type**  | **Description**                                              |
|-------------------|-----------|--------------------------------------------------------------|
| `entity_type_id`  | `integer` | Entity type e.g. `7`, see common API `entity_types`          |
| `entity_id`       | `integer` | Entity ID e.g. sales order number when `entity_type_id` is 7 |

The result will be a [Comments (object)](#comment-object)

**Pagination**

In every response you'll find a path to the next resultset. In the example the next resultset
is `/api/v1/comments/7/1006.json?offset=1`. If `next_resultset` is null no additional data is available.

> HTTP request

```http
GET /api/v1/comments/7/1006.json HTTP/1.1
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
Content-length: 637

{
    "error": false,
    "error_message": null,
    "results": 1,
    "next_resultset": "/api/v1/comments/7/1006.json?offset=1",
    "comments": [
        {
            "comment_id": 227445,
            "comment_type_id": 1,
            "comment_type_name": "Note",
            "employee_id": 46933,
            "entity_id": 1006,
            "entity_type_id": 7,
            "entity_type_name": "Order",
            "comment_type_label": "info",
            "customer_id": 1006,
            "created_at": "2020-05-13 09:32:55",
            "modified_at": "2020-05-13 09:32:55",
            "comment": "Default 10% discount"
        }
    ]
}
```

## Get comments by customer ID

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>/api/v1/customers/:customer_id/comments.json</h6>
    </div>
</div>

| **URI parameter** | **Type**  | **Description**         |
|-------------------|-----------|-------------------------|
| `customer_id`     | `integer` | Customer ID e.g. `1006` |

The result will be a [Comments (object)](#comment-object)

**Pagination**

In every response you'll find a path to the next resultset. In the example the next resultset
is `/api/v1/customers/1006/comments.json?offset=1`. If `next_resultset` is null no additional data is available.

> HTTP request

```http
GET /api/v1/customers/1006/comments.json HTTP/1.1
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
Content-length: 637

{
    "error": false,
    "error_message": null,
    "results": 1,
    "next_resultset": "/api/v1/customers/1006/comments.json?offset=1",
    "comments": [
        {
            "comment_id": 227445,
            "comment_type_id": 1,
            "comment_type_name": "Note",
            "employee_id": 46933,
            "entity_id": 1006,
            "entity_type_id": 7,
            "entity_type_name": "Order",
            "comment_type_label": "info",
            "customer_id": 1006,
            "created_at": "2020-05-13 09:32:55",
            "modified_at": "2020-05-13 09:32:55",
            "comment": "Default 10% discount"
        }
    ]
}
```

## Delete comment

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-delete">DELETE</i>
        <h6>/api/v1/comments/:comment_id.json</h6>
    </div>
</div>

| **URI parameter** | **Type**  | **Description**     |
|-------------------|-----------|---------------------|
| `comment_id`      | `integer` | Comment ID e.g. `6` |

> HTTP request

```http
DELETE /api/v1/comments/6.json HTTP/1.1
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
Content-length: 55

{
    "error": false,
    "error_message": null
    ]
}
```

## Update comment

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-put">PUT</i>
        <h6>/api/v1/comment/227445.json</h6>
    </div>
</div>

> HTTP request

```http
PUT /api/v1/comment/227445.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json

{
    "comment_id": 227445,
    "comment_type_id": 1,
    "employee_id": 46933,
    "comment": "Default 5% discount"
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
Content-length: 55

{
    "error": false,
    "error_message": null
    ]
}
```

## Create comment

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">POST</i>
        <h6>/api/v1/comment/create.json</h6>
    </div>
</div>

> HTTP request

```http
POST /api/v1/comment/create.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json

{
    "comment_type_id": 1,
    "employee_id": 46933,
    "entity_id": 1006,
    "entity_type_id": 7,
    "customer_id": 1006,
    "comment": "Default 8% discount"
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
Content-length: 55

{
    "error": false,
    "error_message": null
    ]
}
```
