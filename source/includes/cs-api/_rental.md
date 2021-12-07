# Rental #

Access rental object data

***Authentication mechanism***

- Basic HTTP Authentication
- Scope(s): `rental`

## Rental objects ##

Get a list of objects available for rental fleet.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v1/rental/objects.json</h6>
	</div>
</div>

> HTTP request

```http
GET /api/v1/rental/objects.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip,deflate
Accept: application/json
Content-type: application/json; charset=utf-8
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 1530

[
    {
        "code": "F1-20297",
        "account_id": 1,
        "article_id": "HT150507",
        "barcode": "8713568237697",
        "store_id": 1,
        "stock_object_id": 20297,
        "is_elo": false,
        "is_moped": false,
        "category_name": "Stadsfietsen",
        "dst_main_id": 1,
        "dst_sub_id": "A",
        "dst_sub_sub_id": 0,
        "is_reserved": false,
        "is_demo": false,
        "is_rental": false,
        "brand_name": "Batavus",
        "frame_type": "Heren",
        "brakes_or_transmission": "",
        "name_brakes": "",
        "object_barcode": "sdgfhdskfvgsil",
        "model_name": "BLOCKBUSTER",
        "color": "Zwart mat",
        "gears": "7",
        "year_description": "2015",
        "size": "",
        "frame_height": "50",
        "wheel_size": "28",
        "frame_size_supplier": "",
        "tyre_size": "",
        "customer_group": "Heren",
        "material_description": "Aluminium",
        "basic_color": "Zwart",
        "basic_color_secondary": "",
        "frame_number": "",
        "chip_number": "",
        "lock_number": "",
        "key_number": "",
        "license_plate_number": "licence_plate",
        "engine_number": "",
        "battery_number": "",
        "images": [
            {
                "date_modified": "2021-01-01T12:00:99",
                "url_thumb": "https://s01.cyclesoftare.nl/link-to-thumb-image.jpg",
                "url_large": "https://s01.cyclesoftare.nl/link-to-image.jpg"
            }
        ]
    }
]
```
