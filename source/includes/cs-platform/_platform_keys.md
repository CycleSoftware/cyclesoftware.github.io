# Platform keys #

Get list of associated stores

***Authentication mechanism***

- Basic HTTP Authentication
- IP filtering
- Scope(s): `platform`

## Properties ##

| Property                                         | Type       | Description                                                 |
|--------------------------------------------------|------------|-------------------------------------------------------------|
| `error_message`                                  | `?string`  | Error if occurred                                           |
| `error`                                          | `boolean`  | `true` if an error has occurred                             |
| `keys`                                           | `object[]` | List of entries                                             |
| `keys[].key`                                     | `string`   | The API key e.g. `Ls6m1ZOgt5JbClmZZHAr8GNhk1qL4Dx0SB7hyyWf` |
| `keys[].is_active`                               | `boolean`  | Whether the API access is enabled `true`                    |
| `keys[].scopes`                                  | `string[]` | The access scopes for this key                              |
| `keys[].store.store_id`                          | `string`   | CS store ID `1-1`                                           |
| `keys[].store.store_gln`                         | `string`   | Global Location Number e.g. `8718288145482`                 |
| `keys[].store.store_name`                        | `string`   | Store name e.g. `CycleSoftware Store`                       |
| `keys[].store.store_address`                     | `string`   | Store address e.g. `Raadhuisplein 1c`                       |
| `keys[].store.store_postal_code`                 | `string`   | Postal code e.g. `5388GM`                                   |
| `keys[].store.store_city`                        | `string`   | City e.g. `Nistelrode`                                      |
| `keys[].store.store_country_code`                | `string`   | Country code e.g. `NL`                                      |
| `keys[].store.store_phone_number`                | `string`   | Phone number e.g. `0733030050`                              |
| `keys[].store.store_email`                       | `string`   | E-mail address.g. `email1@example.nl`                       |
| `keys[].store.store_coordinates`                 | `float[]`  | array with `[latitude, longitude]`                          |
| `keys[].store.store_meta_data`                   | `object`   | Meta data for this entry                                    |
| `keys[].store.store_meta_data.drg_dealer_number` | `string`   | Dynamo Retail Group dealer number e.g. `999`                |


## Keys ##

Get a list of authentication keys

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/platform/authentication/keys.json</h6>
	</div>
</div>

> HTTP request

```http
GET /api/v1/platform/authentication/keys.json HTTP/1.1
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
Content-length: 1626

{
    "error_message": null,
    "error": false,
    "keys": [
        {
            "key": "Ls6m1ZOgt5JbClmZZHAr8GNhk1qL4Dx0SB7hyyWf",
            "is_active": true,
            "scopes": ["platform", "e-commerce"],
            "store": {
                "store_id": "1-3",
                "store_gln": "",
                "store_name": "CycleSoftware",
                "store_address": "Kievitsven 22Z",
                "store_postal_code": "5249JJ",
                "store_city": "Rosmalen",
                "store_country_code": "NL",
                "store_phone_number": "073 303 0050",
                "store_email": "email1@example.nl",
                "store_coordinates": [
                    0,
                    0
                ],
                "store_meta_data": {
                    "drg_dealer_number": "999"
                }
            }
        },
        {
            "key": "BLs6m1ZOgt5JbClmZZHAr8GNhk1qL4Dx0SB7hyyWf",
            "is_active": false,
            "scopes": [],
            "store": {
                "store_id": "1-1",
                "store_gln": "8718288145482",
                "store_name": "CycleSoftware",
                "store_address": "Raadhuisplein 1c",
                "store_postal_code": "5388GM",
                "store_city": "Nistelrode",
                "store_country_code": "NL",
                "store_phone_number": "0733030050",
                "store_email": "email1@example.nl",
                "store_coordinates": [
                    51.701163,
                    5.5619904
                ],
                "store_meta_data": {
                    "drg_dealer_number": "888"
                }
            }
        }
    ]
}
```
