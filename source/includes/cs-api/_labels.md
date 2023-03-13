# Labels #

Attach or detach labels on entities

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `e-commerce`, `common`, `warehouse`

### Label properties

Properties used in create, get and send endpoints.

| Property         | Type      | Nullable | Description                                                  |
|------------------|-----------|----------|--------------------------------------------------------------|
| `error`          | `boolean` | `false`  | `true` if an error occured                                   |
| `error_message`  | `null`    | `true`   | Error message, `null` if no error occured                    |
| `entity_type_id` | `integer` | `false`  | Entity type e.g. `7`, see common API `entity_types`          |
| `entity_id`      | `integer` | `false`  | Entity ID e.g. sales order number when `entity_type_id` is 7 |
| `labels`         | `array`   | `false`  | Array of labels to add                                       |
| `labels[]`       | `string`  | `false`  | Name of the label known in CS e.g. `Label `                  |

## Get entity labels

Get the labels currently attached to the entity

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/labels/:entity_type_id/:entity_id/get.json</h6>
	</div>
</div>

> HTTP request

```http
POST /api/v1/labels/7/51208/get.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 158
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000


{
    "error": false,
    "error_message": null,
    "entity_type_id": 7,
    "entity_id": 51208,
    "labels": [
        "Label 1",
        "Label 2"
    ]
}
```

> HTTP Error Response

```http
HTTP/1.1 400 
Content-type: application/json; charset=utf-8
Content-length: 57
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000


{
    "error": true,
    "error_message": "Bad request"
}
```

## Attach labels

Attach labels to an entity

<div class="api-endpoint">
<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/labels/:entity_type_id/:entity_id/attach.json</h6>
	</div>
</div>

> HTTP request

```http
POST /api/v1/labels/7/51208/attach.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-length: 27 
Content-type: application/json; charset=utf-8

["Label new", "Label new2"]
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 989
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000


{
    "error": false,
    "error_message": null,
    "entity_type_id": 7,
    "entity_id": 51208,
    "labels": [
        "Label 1",
        "Label 2",
        "Label new",
        "Label new2"
    ]
}
```

## Detach labels

Detach labels from an entity

<div class="api-endpoint">
<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/api/v1/labels/:entity_type_id/:entity_id/detach.json</h6>
	</div>
</div>

> HTTP request

```http
POST /api/v1/labels/7/51208/detach.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
Content-type: application/json; charset=utf-8

["Label 1", "Label new2"]
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 160
X-RateLimit-Minutely-Limit: 360
X-RateLimit-Minutely-Remaining: 59
X-RateLimit-Daily-Limit: 15000
X-RateLimit-Daily-Remaining: 14999
X-RateLimit-Daily-Reset: 1678230000


{
    "error": false,
    "error_message": null,
    "entity_type_id": 7,
    "entity_id": 51208,
    "labels": [
        "Label 2",
        "Label new"
    ]
}
```

