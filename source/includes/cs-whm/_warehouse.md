# Warehouse #

Access warehouse data

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `warehouse`

## Available locations ##

Get an overview of capacity and available stock locations

### Properties ###

| Property                                                                     | Type       | Description                                          |
|------------------------------------------------------------------------------|------------|------------------------------------------------------|
| `error`                                                                      | `boolean`  | `true` if error occurred                             |
| `error_message`                                                              | `null`     | Error message if present                             |
| `data.availability`                                                          | `object[]` | Overal availability                                  |
| `data.availability[].code`                                                   | `string`   | Location type code e.g. `elo`                        |
| `data.availability[].description`                                            | `string`   | Location type description e.g. `Elektrische fietsen` |
| `data.availability[].available_locations`                                    | `integer`  | Available locations `830`                            |
| `data.availability_per_warehouse_group`                                      | `object[]` | Availability per warehouse group                     |
| `data.availability_per_warehouse_group[].warehouse_group_name`               | `string`   | e.g. `Groep 1`                                       |
| `data.availability_per_warehouse_group[].availability`                       | `object[]` | Availability within group                            |
| `data.availability_per_warehouse_group[].availability[].code`                | `string`   | Location type code e.g. `elo`                        |
| `data.availability_per_warehouse_group[].availability[].description`         | `string`   | Location type description `Elektrische fietsen`      |
| `data.availability_per_warehouse_group[].availability[].available_locations` | `integer`  | Available locations e.g. `0`                         |

### HTTP request examples ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/warehouse/availability.json</h6>
	</div>
</div>


> Response

```json
{
  "error": false,
  "error_message": null,
  "data": {
    "availability": [
      {
        "code": "elo",
        "description": "Elektrische fietsen",
        "available_locations": 830
      },
      {
        "code": "elo_city",
        "description": "Elektrische fietsen & Stadsfietsen",
        "available_locations": 118
      },
      {
        "code": "cargo",
        "description": "Bakfietsen",
        "available_locations": 0
      },
      {
        "code": "city",
        "description": "Stadsfietsen",
        "available_locations": 4158
      },
      {
        "code": "child_to_20",
        "description": "Kinderfietsen t/m 20inch",
        "available_locations": 161
      },
      {
        "code": "child_above_20",
        "description": "Kinderfietsen vanaf 20inch",
        "available_locations": 0
      }
    ],
    "availability_per_warehouse_group": [
      {
        "warehouse_group_name": "Groep 1",
        "availability": [
          {
            "code": "elo",
            "description": "Elektrische fietsen",
            "available_locations": 0
          },
          {
            "code": "elo_city",
            "description": "Elektrische fietsen & Stadsfietsen",
            "available_locations": 0
          },
          {
            "code": "cargo",
            "description": "Bakfietsen",
            "available_locations": 0
          },
          {
            "code": "city",
            "description": "Stadsfietsen",
            "available_locations": 0
          },
          {
            "code": "child_to_20",
            "description": "Kinderfietsen t/m 20inch",
            "available_locations": 0
          },
          {
            "code": "child_above_20",
            "description": "Kinderfietsen vanaf 20inch",
            "available_locations": 0
          }
        ]
      },
      {
        "warehouse_group_name": "Groep 2",
        "availability": [
          {
            "code": "elo",
            "description": "Elektrische fietsen",
            "available_locations": 720
          },
          {
            "code": "elo_city",
            "description": "Elektrische fietsen & Stadsfietsen",
            "available_locations": 0
          },
          {
            "code": "cargo",
            "description": "Bakfietsen",
            "available_locations": 0
          },
          {
            "code": "city",
            "description": "Stadsfietsen",
            "available_locations": 3951
          },
          {
            "code": "child_to_20",
            "description": "Kinderfietsen t/m 20inch",
            "available_locations": 161
          },
          {
            "code": "child_above_20",
            "description": "Kinderfietsen vanaf 20inch",
            "available_locations": 0
          }
        ]
      }
    ]
  }
}
```
