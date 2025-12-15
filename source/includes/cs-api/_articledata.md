# Article data #

The articledata APIs are designed for pulling article-information for e-commerce environments.

***Authentication***

- Basic HTTP Authentication
- Scope(s): `e-commerce`

## Articledata - V3 ##

From 16-1-2025 we maintain a backwards compatible `v2` & `v3` version of the articledata API.

The backwards compatible versions have minor differences compared to the legacy implementation. The pagination uses a
different token and bicycles may appear in a seperate entry when they contain a barcode.

We advice to migrate to `v4` but will provide the backwards compatible versions.

Get article data available for e-commerce environments or for a specific `barcode`.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/v3/articledata/</h6>
	</div>
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/v3/articledata/:next_resultset</h6>
	</div>
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/v3/articleinfo/:barcode</h6>
	</div>
</div>

**Pagination**

In every response you'll find a path to the next resultset. In the example the next resultset
is `/app/api/v3/articledata/NDg2NjM0NGIzMDg3NjFjZTA1OGVhMGVlYmUzODVlZW/`. If `next_resultset` is null no additional data
is available.

> HTTP Request

```http
GET /app/api/v3/articledata/ HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```json
{
  "error": false,
  "error_message": "",
  "results": 750,
  "next_resultset": "/app/api/v3/articledata/NDg2NjM0NGIzMDg3NjFjZTA1OGVhMGVlYmUzODVlZW/",
  "property_definition": "/app/api/v3/articledata/definition/",
  "supplier_data_columns": [
    "reference",
    "supplier_name",
    "supplier_id",
    "article_id",
    "barcode",
    "brand",
    "model",
    "color",
    "pos_description",
    "size",
    "purchase_price",
    "vat_code",
    "rrp",
    "model_year",
    "product_pos_group_id",
    "main_group",
    "sub_group",
    "sub_sub_group",
    "supplier_sub_group",
    "supplier_subsub_group",
    "order_code",
    "order_quantity",
    "min_order_quantity",
    "status_code",
    "package_contents_quantity",
    "customer_group",
    "keyword",
    {
      "properties": {
        "33": "location",
        "34": "primary_color",
        "35": "secundary_basic_color",
        "36": "weight_bruto",
        "37": "weight_netto",
        "43": "long_description",
        "46": "wheelsize",
        "47": "frametype",
        "105": "keyword",
        "106": "customer_group",
        "108": "model_id",
        "131": "url_article_information",
        "133": "highres_image_url",
        "137": "image_url",
        "139": "video_url",
        "140": "basic_color",
        "141": "size",
        "142": "pos_description",
        "143": "description",
        "203": "width_package",
        "205": "height_package",
        "206": "length_package",
        "232": "user_manual",
        "233": "technical_guide"
      }
    }
  ],
  "data": [
    {
      "modified_at": "26-07-2020",
      "barcode": "0008022142197",
      "parent_barcode": null,
      "is_bicycle": false,
      "bicycle_id": null,
      "has_stock": false,
      "is_discontinued": false,
      "salesprice": "40.75",
      "rrp": "39.95",
      "lease_options": [],
      "removal_fee": "0.00",
      "purchase_price": "0.00",
      "pos_description": "STANDAARD URSUS 26 TWEEPOOT ZWART",
      "brand": "Ursus",
      "promo_salesprice": "0.00",
      "promo_startdate": null,
      "promo_enddate": null,
      "sales_text": "",
      "custom_variable_1": "",
      "custom_variable_2": "",
      "custom_variable_3": "",
      "custom_variable_4": "",
      "custom_variable_5": "",
      "custom_variable_6": "",
      "images": [
        {
          "date_modified": "08-05-2012 08:02:58",
          "url_thumb": "http://s02.cyclesoftware.nl/app/img/Y/artPic_public_T_18563.jpg",
          "url_large": "http://s02.cyclesoftware.nl/app/img/Y/artPic_public_L_18563.jpg"
        }
      ],
      "product_group_main": "O&A",
      "product_group_sub": "Onderdelen/Reparatie",
      "product_group_sub_sub": "Standaarden",
      "product_group_id": "2_N_1",
      "product_pos_group_id": "21",
      "article_location": null,
      "supplier_data": [
        [
          "7177049",
          "ACCELL NL",
          "5229",
          "680862",
          "0008022142197",
          "URSUS",
          "JUMBO",
          "ZWART",
          "STANDAARD URSUS 26 JUMBO TWEEPOOT ZWART",
          "",
          "0.00",
          "H",
          "39.95",
          "0",
          "21",
          "O&A",
          "Onderdelen/Reparatie",
          "Standaarden",
          null,
          null,
          "",
          "1",
          "1",
          "VERVALLEN",
          "1",
          "",
          "STANDAARD",
          {
            "34": "ZWART",
            "43": "STANDAARD URSUS 26 JUMBO TWEEPOOT ZWART",
            "105": "STANDAARD",
            "137": [
              "http://www.accentry.com/upload/Juncker/680862.JPG"
            ],
            "140": "ZWART",
            "142": "STANDAARD URSUS 26 JUMBO",
            "143": "STANDAARD URSUS 26 JUMBO TWEEPOOT ZWART"
          }
        ]
      ]
    },
    {
      "modified_at": "10-02-2022",
      "barcode": "0091021578005",
      "parent_barcode": null,
      "is_bicycle": false,
      "bicycle_id": null,
      "has_stock": false,
      "is_discontinued": false,
      "salesprice": "139.95",
      "rrp": "139.95",
      "lease_options": [],
      "removal_fee": "0.00",
      "purchase_price": "0.00",
      "pos_description": "Thule yepp kinderzitje nexxt maxi bagagedrager vib",
      "brand": "THULE",
      "promo_salesprice": "0.00",
      "promo_startdate": null,
      "promo_enddate": null,
      "sales_text": "",
      "custom_variable_1": "",
      "custom_variable_2": "",
      "custom_variable_3": "",
      "custom_variable_4": "",
      "custom_variable_5": "",
      "custom_variable_6": "",
      "images": [
        {
          "date_modified": "12-02-2019 11:03:31",
          "url_thumb": "http://s02.cyclesoftware.nl/app/img/Y/artPic_public_T_1741674.jpg",
          "url_large": "http://s02.cyclesoftware.nl/app/img/Y/artPic_public_L_1741674.jpg"
        }
      ],
      "product_group_main": "O&A",
      "product_group_sub": "Kinderzitjes",
      "product_group_sub_sub": "Kinderzitje achter",
      "product_group_id": "2_D_2",
      "product_pos_group_id": "21",
      "article_location": null,
      "supplier_data": [
        [
          "7967511",
          "THULE",
          "5285",
          "12080205",
          "0091021578005",
          "THULE",
          "Yepp Nexxt Maxi Universal Mount Vibrant Orange",
          "",
          "Yepp Nexxt Maxi Universal Mount Vibrant Orange",
          "",
          "0.00",
          "H",
          "139.95",
          "0",
          "21",
          "O&A",
          "Kinderzitjes",
          "Kinderzitje achter",
          null,
          null,
          "",
          "1",
          "1",
          "COURANT",
          "1",
          "",
          "ZITJE",
          {
            "36": "3.73",
            "37": "2.70",
            "43": "\"Lichtgewicht en veilig fietszitje voor montage op de bagagedrager met een eigentijds ontwerp dat hoogwaardig comfort voor uw kind biedt.\"",
            "105": "ZITJE",
            "131": "https://www.thule.com/nl-nl/nl/child-bike-seats/rear-mounted-child-bike-seats/thule-yepp-nexxt-maxi-_-12080205",
            "133": [
              "https://cdn1.static-tgdp.com/ui/productimages/Approved/std.lang.all/44/49/604449_sized_900x600.jpg"
            ],
            "137": [
              "https://cdn1.static-tgdp.com/ui/productimages/Approved/std.lang.all/44/49/604449_sized_900x600.jpg"
            ],
            "139": [
              "https://www.youtube.com/embed/6KGMZFZW58E"
            ],
            "142": "Yepp Nexxt Maxi Universal",
            "143": "Yepp Nexxt Maxi Universal Mount Vibrant Orange",
            "203": "0.43",
            "205": "0.89",
            "206": "0.28",
            "232": [
              {
                "type": "GEBRUIKERS HANDLEIDING",
                "type_omschrijving": "Gebruikers handleiding",
                "url": "https://www.thule.com/assetloader.axd?pimid=12080205&id=574173&brand=Thule&market=NL&att=1"
              }
            ],
            "233": [
              {
                "type": "SERVICE DOCUMENTATIE",
                "type_omschrijving": "Service documentatie",
                "url": "https://www.thule.com/assetloader.axd?pimid=12080205&id=580543&brand=Thule&market=NL&att=1"
              }
            ]
          }
        ],
        [
          "7996325",
          "AGU",
          "1",
          "130383",
          "0091021578005",
          "THULE",
          "",
          "Oranje",
          "Thule yepp kinderzitje nexxt maxi bagagedrager vib",
          "",
          "0.00",
          "H",
          "139.95",
          "0",
          "21",
          "O&A",
          "Kinderzitjes",
          "Kinderzitje achter",
          null,
          null,
          "130383",
          "0",
          "0",
          "VERVALLEN",
          "0",
          "",
          "ZITJE",
          {
            "33": "A",
            "34": "ORANJE",
            "36": "3.50",
            "37": "3.00",
            "43": "Lichtgewicht en veilig fietszitje, voor montage op de bagagedrager, met een eigentijds ontwerp dat hoogwaardig comfort voor uw kind biedt.<b>Specificaties</b>\u2022 Merk: Thule\u2022 Upgrade: nvt\u2022 Introductiejaar: 2017\u2022 Alternatief: Thule Yepp Nexxt\u2022 Kleur: Oranje\u2022 Locatie Fiets: Achter\u2022 Montage: Bagagedrager\u2022 Diameter Bevestiging: nvt\u2022 Inhoud Pakket: Compleet FietszitjeVoor alle specificaties, kijk onderaan de pagina.<b>USP</b>- Maximaal comfort voor uw kind en een veilige en goede pasvorm dankzij de verstelbare, vijfpuntsgordel met zachte schouderpads - Biedt uw kind een soepele rit in het zachte en schokabsorberende zitje - Lichtgewicht maar robuust zitje waarin een harde buitenkant wordt gecombineerd met een zachte zitting voor optimaal comfort voor het kind - Zet uw kind zeer snel, gemakkelijk en handig vast met de magnetische kindveilige gesp - Gemak en flexibiliteit zijn verzekerd naarmate ...",
            "105": "ZITJE",
            "137": [
              "http://www.abcb2b.eu/afbeelding.aspx?a=130383&t=jpgextra"
            ],
            "140": "Oranje",
            "142": "ORANJE Zitje",
            "143": "Thule yepp kinderzitje nexxt maxi bagagedrager vib"
          }
        ]
      ]
    },
    {
      "modified_at": "08-03-2021",
      "barcode": "0193751005308",
      "parent_barcode": null,
      "is_bicycle": false,
      "bicycle_id": null,
      "has_stock": false,
      "is_discontinued": false,
      "salesprice": "39.90",
      "rrp": "39.90",
      "lease_options": [],
      "removal_fee": "0.00",
      "purchase_price": "0.00",
      "pos_description": null,
      "brand": "TANNUS",
      "promo_salesprice": "0.00",
      "promo_startdate": null,
      "promo_enddate": null,
      "sales_text": "",
      "custom_variable_1": "",
      "custom_variable_2": "",
      "custom_variable_3": "",
      "custom_variable_4": "",
      "custom_variable_5": "",
      "custom_variable_6": "",
      "images": [],
      "product_group_main": "O&A",
      "product_group_sub": "Banden",
      "product_group_sub_sub": "Banden accessoires en onderdelen",
      "product_group_id": "2_A_3",
      "product_pos_group_id": "21",
      "article_location": null,
      "supplier_data": [
        [
          "9650393",
          "GRANSIERBV",
          "7069",
          "30129528",
          "0193751005308",
          "TANNUS",
          "",
          "Rood",
          "Armour 3 in 1 fietsband anti-lek systeem 28 x 1.65",
          "28\"",
          "0.00",
          "H",
          "39.90",
          "0",
          "21",
          "O&A",
          "Banden",
          "Banden accessoires en onderdelen",
          null,
          null,
          "30129528",
          "1",
          "1",
          "COURANT",
          "1",
          "",
          "VELGLINT",
          {
            "34": "ROOD",
            "43": "Rij sneller en met meer vertrouwen met het Armour anti-lek systeem van Tannus. Deze extra beschermlaag wordt tussen de binnen- en buitenband geplaatst. Herbruikbaar Eenvoudige montage tussen band en binnenband Hogere grip en lagere rolweerstand Heel licht All-round anti-lekbescherming Universeel voor de bandengrootte 28x 1.65 - 1.85, 42/47-700. De aanbevolen binnenbandgrootte is 28/40-622. Past in de velgmaten 19/25-622.",
            "105": "VELGLINT",
            "131": "https://www.gransier.nl/nl/tannus-armour-3-in-1-fietsband-anti-lek-systeem-28-x-1-65-1-85-700-x-42-47c",
            "133": null,
            "140": "Rood",
            "141": "28\"",
            "142": "Armour 3 in 1 fietsband",
            "143": "Armour 3 in 1 fietsband anti-lek systeem 28 x 1.65"
          }
        ]
      ]
    }
  ]
}
```

## Articledata definitions - V3 ##

Use `/app/api/v3/articledata/definition/` and `/app/api/groups/`  for more information about possible field values.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/v3/articledata/definition/</h6>
	</div>
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/app/api/groups/</h6>
	</div>
</div>


**Main object**

| **Element**             | **Description**                                                  |
|-------------------------|------------------------------------------------------------------|
| `error`                 | boolean                                                          |
| `error_message`         | Error message description                                        |
| `results`               | Number of results (max 750)                                      |
| `next_result_set`       | Next result set url e.g. /load/ci_app/api/article_data/750-750-0 |
| `supplier_data_columns` | Definition of fields used in supplier_data element               |

**Data object**

| **Property**            | **Description**                                                                         | **Length**                        |
|-------------------------|-----------------------------------------------------------------------------------------|-----------------------------------|
| `barcode`               | Article barcode (alpha numeric)                                                         | 20                                |
| `parent_barcode`        |                                                                                         | 20                                |
| `is_bicycle`            | Boolean article is bicycle                                                              |                                   |
| `bicycle_id`            | Multiple unique bicycle identifiers                                                     | 0..*                              |
| `salesprice`            | Price without promo                                                                     | decimal string                    |
| `has_stock`             | Boolean, if true there is stock for this article at supplier                            |                                   |
| `is_discontinued`       | Boolean, whether the article is marked by dealer as discontinued                        |                                   |
| `rrp`                   | Recommended Retail Price                                                                | decimal string                    |
| `lease_options`         | List of objects with lease option                                                       |                                   |
| `removal_fee`           | The default removal fee for elo bikes                                                   | decimal string                    |
| `pos_description`       | Description used in POS and Invoices                                                    | 255                               |
| `brand`                 | Brand name                                                                              | 30                                |
| `promo_salesprice`      | Promo price                                                                             | decimal string                    |
| `promo_startdate`       | yyyy-mm-dd hh:mm:ss                                                                     | 19                                |
| `promo_enddate`         | yyyy-mm-dd hh:mm:ss                                                                     | 19                                |
| `sales_text`            | Product description                                                                     | 10000                             |
| `custom_variable_1`     | Custom defined variable                                                                 | 100                               |
| `custom_variable_2`     | Custom defined variable                                                                 | 100                               |
| `custom_variable_3`     | Custom defined variable                                                                 | 100                               |
| `custom_variable_4`     | Custom defined variable                                                                 | 100                               |
| `custom_variable_5`     | Custom defined variable                                                                 | 100                               |
| `images`                | Object with image urls see images object                                                |                                   |
| `product_group_main`    | DST main group description                                                              | 40                                |
| `product_group_sub`     | DST sub group description                                                               | 40                                |
| `product_group_sub_sub` | DST sub sub group description                                                           | 80                                |
| `product_group_id`      | DST group code                                                                          | 8                                 |
| `product_pos_group_id`  | POS sales group see request /load/ci_app/api/groups                                     | 1 = new product 20 = used product |
| `supplier_data`         | Supplier data object, the field columns are defined in the supplier_data_columns column | 0..*                              |

**Lease option object**

| **Property**         | **Description**                                                                       | **Type**                                                        |
|----------------------|---------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| `type`               | b2b or b2c                                                                            | String                                                          |
| `platform`           | Name of the lease platform e.g. “cyclelease”                                          | String                                                          |
| `rrp`                | RRP used to calculate the fee                                                         | Decimal string                                                  |
| `duration_months`    | Contract length                                                                       | Integer                                                         |
| `fee_monthly_ex_vat` | The estimated base lease fee ex vat                                                   | Decimal string                                                  |
| `service`            | Services included                                                                     | List of strings                                                 |
| `options`            | Additional selectable options with description and fee_monthly_ex_vat for each option | List of object with elements description and fee_monthly_ex_vat |

**Images object**

| **Property**    | **Description**     | **Length** |
|-----------------|---------------------|------------|
| `date_modified` | dd-mm-yyyy hh:mm:ss | 19         |
| `url_thumb`     | url to thumb image  | 100        |
| `url_large`     | url to large image  | 100        |

<aside class="notice">
When a image is requested we send a http header back called 'Etag' we advice to store this hash with the image url.
When the image is requested again we check if the Etag has changed, if not we return a 304 http status code and no image
data.
This will save you bandwidth and time.
</aside>

**Supplier_data object**

| **Property**                        | **Description**                              |
|-------------------------------------|----------------------------------------------|
| `reference`                         | ID of article, or reference to bicycle       |
| `supplier_name`                     | Supplier name                                |
| `supplier_id`                       | Supplier id (see groups api)                 |
| `article_id`                        | Article code                                 |
| `barcode`                           | Barcode (ean, upc or string)                 |
| `brand`                             | Brand name                                   |
| `model`                             | Model name                                   |
| `color`                             | Color                                        |
| `pos_description`                   | Description used in POS                      |
| `size`                              | Size                                         |
| `purchase_price`                    | Purchase price (= null)                      |
| `vat_code`                          | Code: H, L, G                                |
| `rrp`                               | Recommended retail price                     |
| `model_year`                        | Year of model                                |
| `product_pos_group_id`              | Group id of POS group (see groups api)       |
| `main_group`                        | DST main group                               |
| `sub_group`                         | DST sub group                                |
| `sub_sub_group`                     | DST subsub group                             |
| `supplier_sub_group`                | Supplier groupname                           |
| `supplier_subsub_group`             | Supplier sub groupname                       |
| `order_code`                        | Order code, see also article_id              |
| `order_quantity`                    | Quantity in which it is ordered at supplier  |
| `min_order_quantity`                | Minimal order quantity for order to supplier |
| `status_code`                       | Status code (current = COURANT)              |
| `package_contents_quantity`         | If multiple items in package                 |
| `customer_group`                    | Customer group name (Heren, Dames etc)       |
| `keyword`                           | Key description word (e.g. FIETS)            |
| `basic_color`                       | Basic color description                      |
| `primary_color`                     | Basic color description                      |
| `secundary_basic_color`             | Secundary color description                  |
| `weight_bruto`                      | Weight kg                                    |
| `weight_netto`                      | Weight net kg                                |
| `description`                       | Description of product                       |
| `wheelsize`                         | Wheelsize in inch                            |
| `frametype`                         | Frametype (e.g. HEREN, DAMES)                |
| `framesize`                         | Framesize in cm                              |
| `framesize_description`             | Framesize description                        |
| `material`                          | Frame material                               |
| `brand_gearsystem_rear`             | Brand of gear rear                           |
| `model_gearsystem_rear`             | Model of gear rear                           |
| `type_gearsystem_rear`              | Type of gear rear                            |
| `gears`                             | Number of gears                              |
| `brand_primary_brake_system_rear`   | Brand of primary brake rear                  |
| `type_primary_brake_system_rear`    | Type of primary brake rear                   |
| `model_primary_brake_system_rear`   | Model of primary brake rear                  |
| `brand_secondary_brake_system_rear` | Brand of secondary brake rear                |
| `type_secondary_brake_system_rear`  | Type of secondary brake rear                 |
| `model_secondary_brake_system_rear` | Model of secondary brake rear                |
| `brand_brake_system_front`          | Brand of primary brake front                 |
| `model_brake_system_front`          | Type of primary brake front                  |
| `type_brake_system_front`           | Model of primary brake front                 |

## Articledata - V4 ##

Get article data available for e-commerce environments or for a specific `barcode`.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v4/articledata/entries.json</h6>
	</div>
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v4/articledata/entries.json?token=:token</h6>
	</div>
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v4/articledata/entries.json?barcode=:barcode</h6>
	</div>
</div>

| GET parameter        | Type      | Description                                                                       |
|----------------------|-----------|-----------------------------------------------------------------------------------|
| `:modified_since`    | `integer` | Only return entries with modification after this value (20241213000000)           |
| `:barcode`           | `string`  | Only return entry for specific barcode                                            |
| `:exclude_ecommerce` | `boolean` | If `true` exclude ecommerce information (defaults to `false`)                     |
| `:exclude_articles`  | `boolean` | If `true` exclude articles (defaults to `false`)                                  |
| `:exclude_objects`   | `boolean` | If `true` exclude objects / bicycles (defaults to `false`)                        |
| `:per_store_id`      | `boolean` | If `true` only return for store associated with credentials (defaults to `false`) |

**Important***

- Stock only present for non-objects
- Objects lists the available stock objects

### Response properties ###

| Property                                                        | Type         | Omittable | Description                                                                                                                                |
|-----------------------------------------------------------------|--------------|-----------|--------------------------------------------------------------------------------------------------------------------------------------------|
| `data`                                                          | `object[]`   | `false`   |                                                                                                                                            |
| `data[].modified_at`                                            | `datetime`   | `false`   | Last modification of underlying data e.g. `2024-07-24 16:23:45`                                                                            |
| `data[].barcode`                                                | `string`     | `false`   | The barcode of the article e.g. `5400928076890` (usually an EAN code)                                                                      |
| `data[].pricing`                                                | `object`     | `false`   | Object with pricing information about the article`                                                                                         |
| `data[].pricing.currency`                                       | `string`     | `false`   | The currency code e.g. `EUR`                                                                                                               |
| `data[].pricing.rrp_cents`                                      | `integer`    | `false`   | Recommended retail price in cents e.g. `269900`                                                                                            |
| `data[].pricing.pos_sales_price_cents`                          | `integer`    | `false`   | POS sales price in cents e.g. `269900`                                                                                                     |
| `data[].pricing.ecommerce_price_cents`                          | `integer`    | `true`    | E-commerce sales price in cents e.g. `269900`                                                                                              |
| `data[].pricing.purchase_price_cents`                           | `integer`    | `true`    | Purchase price in cents (excluding VAT) e.g. `99500`                                                                                       |
| `data[].pricing.pos_group_id`                                   | `integer`    | `false`   | POS group ID e.g. `1` (see common enum)                                                                                                    |
| `data[].pricing.vat_code`                                       | `?integer`   | `true`    | VAT code if specified e.g. `2`, if no specified the default VAT-code of POS group is applied                                               |
| `data[].pricing.pos_promo_price_cents`                          | `?integer`   | `true`    | POS promo price in cents e.g. `4000`                                                                                                       |
| `data[].pricing.pos_promo_price_from`                           | `?date`      | `true`    | POS promo start date e.g. `2024-07-03`                                                                                                     |
| `data[].pricing.pos_promo_price_until`                          | `?date`      | `true`    | POS promo end date e.g. `2024-10-19`                                                                                                       |
| `data[].pricing.ecommerce_promo_price_cents`                    | `?integer`   | `true`    | E-commerce promo price in cents e.g. `3900`                                                                                                |
| `data[].pricing.ecommerce_promo_price_from`                     | `?date`      | `true`    | E-commerce promo start date e.g. `2024-07-01`                                                                                              |
| `data[].pricing.ecommerce_promo_price_until`                    | `?date`      | `true`    | E-commerce promo end date e.g. `2024-10-19`                                                                                                |
| `data[].objects`                                                | `?object[]`  | `false`   | When the article is an object (bicycle, moped) this element is present and contains unique objects                                         |
| `data[].objects[].object_code`                                  | `string`     | `false`   | The object code with account and object_id e.g. `F.1-232432`                                                                               |
| `data[].objects[].object_id`                                    | `integer`    | `false`   | The unique object_id within account e.g. `232432`                                                                                          |
| `data[].objects[].store_id`                                     | `integer`    | `false`   | Store ID e.g. `1`                                                                                                                          |
| `data[].objects[].available`                                    | `boolean`    | `false`   | `true` if the object is available (in stock, not sold and not reserved) e.g. `true`                                                        |
| `data[].objects[].expected_at`                                  | `date`       | `true`    | Expected delivery date or null .e.g. `2024-10-01`                                                                                          |
| `data[].objects[].is_demo`                                      | `boolean`    | `false`   | `true` if object is a demo object e.g. `false`                                                                                             |
| `data[].objects[].is_used`                                      | `boolean`    | `false`   | `true` if the object is used e.g. `false`                                                                                                  |
| `data[].objects[].currency`                                     | `string`     | `false`   | Currency code e.g. `EUR`                                                                                                                   |
| `data[].objects[].ecommerce_price_cents`                        | `integer`    | `false`   | E-commerce price in cents e.g. `269900`                                                                                                    |
| `data[].objects[].pos_sales_price_cents`                        | `integer`    | `false`   | POS sales price in cents e.g. `269900`                                                                                                     |
| `data[].objects[].purchase_price_cents`                         | `integer`    | `true`    | Purchase price in cents e.g. `0`                                                                                                           |
| `data[].objects[].km_age`                                       | `?integer`   | `false`   | KM age e.g. `100` or `null` when not available                                                                                             |
| `data[].objects[].identification`                               | `object`     | `false`   | Object with identifications, may be an empty object if no values available                                                                 |
| `data[].objects[].identification.battery_number`                | `string`     | `true`    | The battery number if set                                                                                                                  |
| `data[].objects[].identification.battery_number_2`              | `string`     | `true`    | The battery number_2 if set                                                                                                                |
| `data[].objects[].identification.engine_number`                 | `string`     | `true`    | The engine number if set                                                                                                                   |
| `data[].objects[].identification.frame_number`                  | `string`     | `true`    | The frame number if set                                                                                                                    |
| `data[].objects[].identification.imei_number`                   | `string`     | `true`    | The imei number if set                                                                                                                     |
| `data[].objects[].identification.key_number`                    | `string`     | `true`    | The key number if set                                                                                                                      |
| `data[].objects[].identification.key_number_2`                  | `string`     | `true`    | The key number_2 if set                                                                                                                    |
| `data[].objects[].identification.license_plate_number`          | `string`     | `true`    | The license plat if set if set                                                                                                             |
| `data[].objects[].identification.lock_number`                   | `string`     | `true`    | The lock number if set                                                                                                                     |
| `data[].objects[].identification.lock_number_2`                 | `string`     | `true`    | The lock number_2 if set                                                                                                                   |
| `data[].objects[].identification.serial_number`                 | `string`     | `true`    | The serial number if set                                                                                                                   |
| `data[].objects[].identification.velopass_code`                 | `string`     | `true`    | The velopass code if set                                                                                                                   |
| `data[].suppliers`                                              | `object[]`   | `false`   | List of suppliers associated with the article                                                                                              |
| `data[].suppliers[]._id`                                        | `integer`    | `false`   | Internal ID e.g. `11043281`                                                                                                                |
| `data[].suppliers[].supplier_id`                                | `integer`    | `false`   | Supplier ID e.g. `13005` (see common supplier list)                                                                                        |
| `data[].suppliers[].supplier_name`                              | `string`     | `false`   | Supplier code name e.g. `BELGIAN CYCLING FACTORY`                                                                                          |
| `data[].suppliers[].article_id`                                 | `string`     | `false`   | Article number e.g. `SBIELARID023`                                                                                                         |
| `data[].suppliers[].model_id`                                   | `null`       | `true`    | Model ID, if other entries have the same model_id they could be grouped                                                                    |
| `data[].suppliers[].parent_barcode`                             | `null`       | `true`    | Parent barcode (if grouped within model_id)                                                                                                |
| `data[].suppliers[].currency`                                   | `string`     | `false`   | Currency code e.g. `EUR`                                                                                                                   |
| `data[].suppliers[].rrp_cents`                                  | `integer`    | `false`   | Recommended retail price in cents e.g. `269900`                                                                                            |
| `data[].suppliers[].purchase_price_cents`                       | `integer`    | `false`   | Purchase price in cents e.g. `0`                                                                                                           |
| `data[].suppliers[].package.package_contents`                   | `integer`    | `false`   | Number of consumer goods within delivery from supplier e.g. `1`                                                                            |
| `data[].suppliers[].package.min_order_quantity`                 | `integer`    | `false`   | Minimal order quantity for this supplier e.g. `1`                                                                                          |
| `data[].suppliers[].package.order_unit`                         | `integer`    | `false`   | Order unit for this supplier e.g. `1`                                                                                                      |
| `data[].properties<:property_name>.type`                        | `string`     | `false`   | The data type of the property e.g. `codelist:article_main_group` (see `Data-types` for possible types)                                     |
| `data[].properties<:property_name>.unit`                        | `?string`    | `true`    | The unit of data e.g. `kg` or `cm` if available.                                                                                           |
| `data[].properties<:property_name>.values`                      | `object[]`   | `false`   | Different values for the property (different values may be present sourced from different suppliers and or objects)                        |
| `data[].properties<:property_name>.values[].supplier_ids`       | `?integer[]` | `true`    | The list of supplier-ids which have this property in their article definition                                                              |
| `data[].properties<:property_name>.values[].object_ids`         | `?integer[]` | `true`    | The list of object-ids which have this property in their definition                                                                        |
| `data[].properties<:property_name>.values[].code`               | `?string`    | `true`    | If the data-type refers to a code list, this is the code value e.g. `1`                                                                    |
| `data[].properties<:property_name>.values[].code_international` | `?string`    | `true`    | If the data-type refers to a code list, this is the international code value e.g. `1`                                                      |
| `data[].properties<:property_name>.values[].value`              | `mixed`      | `false`   | The value of the property, the structure depends on `data[].properties<:property_name>.type` e.g. `2021`                                   |
| `data[].stock`                                                  | `?object`    | `false`   | Only present for non object entries, contains stock information within stores                                                              |
| `data[].stock.available`                                        | `boolean`    | `false`   | `true` if there is stock available within stores e.g. `false`                                                                              |
| `data[].stock.stores`                                           | `object`     | `false`   | Array with object information per store-id                                                                                                 |
| `data[].stock.stores[].store_id`                                | `integer`    | `false`   | Store ID e.g. `1`                                                                                                                          |
| `data[].stock.stores[].stock_level`                             | `integer`    | `false`   | Stock level in this store e.g. `0`                                                                                                         |
| `data[].stock.stores[].locations`                               | `array`      | `false`   | Stock locations associated with this article                                                                                               |
| `data[].stock.stores[].locations[].store_id`                    | `integer`    | `false`   | e.g. `1`                                                                                                                                   |
| `data[].stock.stores[].locations[].location_id`                 | `integer`    | `false`   | ID of the location e.g. `3`                                                                                                                |
| `data[].stock.stores[].locations[].location_x`                  | `integer`    | `false`   | Location x-axis e.g. `1`                                                                                                                   |
| `data[].stock.stores[].locations[].location_y`                  | `integer`    | `false`   | Location y-axis e.g. `2`                                                                                                                   |
| `data[].stock.stores[].locations[].location_capacity`           | `integer`    | `false`   | Capacity e.g. `33`                                                                                                                         |
| `data[].stock.stores[].locations[].location_bulk`               | `string`     | `false`   | Bulk location name e.g. `Magazijn`                                                                                                         |
| `pagination.next_url`                                           | `?string`    | `true`    | If there is more data this is the URL to the next API request. `https://api.cyclesoftware.nl/api/v4/articledata/entries.json?token=abc...` |

> HTTP Request

```http
GET /api/v4/articledata/entries.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```json
{
  "data": [
    {
      "modified_at": "2024-07-24 16:23:45",
      "barcode": "5400928076890",
      "pricing": {
        "currency": "EUR",
        "rrp_cents": 269900,
        "pos_sales_price_cents": 269900,
        "ecommerce_price_cents": 269900,
        "purchase_price_cents": 100,
        "pos_group_id": 1,
        "vat_code": 2
      },
      "objects": [
        {
          "object_code": "F.1-232432",
          "object_id": 232432,
          "store_id": 1,
          "available": true,
          "expected_at": null,
          "is_demo": false,
          "is_used": false,
          "currency": "EUR",
          "ecommerce_price_cents": 269900,
          "pos_sales_price_cents": 269900,
          "purchase_price_cents": 100,
          "km_age": null,
          "identification": {
            "frame_number": "0023232",
            "key_number": "K3323"
          }
        }
      ],
      "suppliers": [
        {
          "_id": 11043281,
          "supplier_id": 13005,
          "supplier_name": "BELGIAN CYCLING FACTORY",
          "article_id": "SBIELARID023",
          "model_id": null,
          "parent_barcode": null,
          "currency": "EUR",
          "rrp_cents": 269900,
          "purchase_price_cents": 100,
          "package": {
            "package_contents": 1,
            "min_order_quantity": 1,
            "order_unit": 1
          }
        }
      ],
      "properties": {
        "article_main_group": {
          "type": "codelist:article_main_group",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "object_ids": [
                232432
              ],
              "code": "1",
              "code_international": "1",
              "value": {
                "nl": "Fietsen",
                "en": "Bikes",
                "fr": "Vélos"
              }
            }
          ]
        },
        "article_group": {
          "type": "codelist:article_group",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "object_ids": [
                232432
              ],
              "code": "1A",
              "code_international": "1A",
              "value": {
                "nl": "Stadsfietsen",
                "en": "Citybike",
                "fr": "Vélos De Ville"
              }
            }
          ]
        },
        "article_sub_group": {
          "type": "codelist:article_sub_group",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "object_ids": [
                232432
              ],
              "code": "1A00",
              "code_international": "1A00",
              "value": {
                "nl": "Stadsfiets",
                "en": "City bike without gear or with hub gear",
                "fr": "Vélo de Ville"
              }
            }
          ]
        },
        "model_year": {
          "type": "integer",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "object_ids": [
                232432
              ],
              "value": 2021
            }
          ]
        },
        "basic_color": {
          "type": "codelist:base_color",
          "values": [
            {
              "object_ids": [
                232432
              ],
              "code": "ZWART",
              "code_international": "BLACK",
              "value": {
                "nl": "Zwart",
                "en": "Black",
                "fr": "Noir"
              }
            },
            {
              "supplier_ids": [
                13005
              ],
              "value": "Black Powder Coating // Alumin"
            }
          ]
        },
        "description": {
          "type": "string",
          "values": [
            {
              "object_ids": [
                232432
              ],
              "value": {
                "user": "Ridley Elykx A Black Powder Coating // Aluminium B"
              }
            },
            {
              "supplier_ids": [
                13005
              ],
              "value": {
                "nl": "Ridley Elykx A Black Powder Coating // Aluminium Bikes Only // PC8 2021"
              }
            }
          ]
        },
        "frametype": {
          "type": "codelist:frame",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "object_ids": [
                232432
              ],
              "code": "UNI",
              "code_international": "UNI",
              "value": {
                "nl": "Uni",
                "en": "Unisex",
                "fr": "Uni"
              }
            }
          ]
        },
        "framesize_description": {
          "type": "localized-strings",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "object_ids": [
                232432
              ],
              "value": {
                "user": "L"
              }
            }
          ]
        },
        "gears": {
          "type": "integer",
          "values": [
            {
              "object_ids": [
                232432
              ],
              "value": 0
            }
          ]
        },
        "keyword": {
          "type": "codelist:keyword",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "code": "FIETS",
              "code_international": "BICYCLE",
              "value": {
                "nl": "Fiets",
                "en": "Bicycle",
                "fr": "Vélo"
              }
            }
          ]
        },
        "brand": {
          "type": "codelist:brand",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "value": "Ridley"
            }
          ]
        },
        "model": {
          "type": "localized-strings",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "value": {
                "nl": "Elykx A"
              }
            }
          ]
        },
        "image_url": {
          "type": "string[]",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "value": [
                "https://images.cyclingfactory.be/SBIELARID023_image_2048x.jpg"
              ]
            }
          ]
        },
        "color_description": {
          "type": "localized-strings",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "value": {
                "nl": "ZWART"
              }
            }
          ]
        },
        "pos_description": {
          "type": "localized-strings",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "value": {
                "nl": "Ridley Elykx A Black Powder Coating // Aluminium"
              }
            }
          ]
        },
        "gearsystem_rear_model": {
          "type": "localized-strings",
          "values": [
            {
              "supplier_ids": [
                13005
              ],
              "value": {
                "nl": "Shimano XT"
              }
            }
          ]
        }
      }
    },
    {
      "modified_at": "2024-07-24 16:26:35",
      "barcode": "0008022142197",
      "pricing": {
        "currency": "EUR",
        "rrp_cents": 3995,
        "pos_sales_price_cents": 4075,
        "pos_promo_price_cents": 4000,
        "pos_promo_price_from": "2024-07-03",
        "pos_promo_price_until": "2024-10-19",
        "ecommerce_price_cents": 4075,
        "ecommerce_promo_price_cents": 3900,
        "ecommerce_promo_price_from": "2024-07-01",
        "ecommerce_promo_price_until": "2024-10-19",
        "purchase_price_cents": 100,
        "pos_group_id": 21
      },
      "stock": {
        "available": false,
        "stores": [
          {
            "store_id": 1,
            "stock_level": 0,
            "locations": [
              {
                "store_id": 1,
                "location_id": 3,
                "location_x": 1,
                "location_y": 2,
                "location_capacity": 33,
                "location_bulk": "Magazijn"
              }
            ]
          },
          {
            "store_id": 2,
            "stock_level": 0,
            "locations": []
          },
          {
            "store_id": 3,
            "stock_level": 0,
            "locations": []
          }
        ]
      },
      "suppliers": [
        {
          "_id": 7177049,
          "supplier_id": 5229,
          "supplier_name": "ACCELL NL",
          "article_id": "680862",
          "model_id": null,
          "parent_barcode": null,
          "currency": "EUR",
          "rrp_cents": 3995,
          "purchase_price_cents": 100,
          "package": {
            "package_contents": 1,
            "min_order_quantity": 1,
            "order_unit": 1
          }
        }
      ],
      "properties": {
        "images": {
          "type": "image[]",
          "values": [
            {
              "value": [
                {
                  "date_modified": "2012-05-08 08:02:58",
                  "url_thumb": "https://cdn.cyclesoftware.nl/app/img/Y/artPic_public_T_18563.jpg",
                  "url_large": "https://cdn.cyclesoftware.nl/app/img/Y/artPic_public_L_18563.jpg"
                }
              ]
            }
          ]
        },
        "pos_description": {
          "type": "localized-strings",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "value": {
                "user": "STANDAARD URSUS 26 JUMBO",
                "nl": "STANDAARD URSUS 26 TWEEPOOT ZWART nl_NL"
              }
            },
            {
              "supplier_ids": [
                5229
              ],
              "value": {
                "nl": "STANDAARD URSUS 26 JUMBO"
              }
            }
          ]
        },
        "brand": {
          "type": "codelist:brand",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "value": "URSUS"
            }
          ]
        },
        "article_main_group": {
          "type": "codelist:article_main_group",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "code": "2",
              "code_international": "2",
              "value": {
                "nl": "O&A",
                "en": "Parts and accessories",
                "fr": "Pièces et accessoires"
              }
            }
          ]
        },
        "article_group": {
          "type": "codelist:article_group",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "code": "2N",
              "code_international": "2N",
              "value": {
                "nl": "Onderdelen/Reparatie",
                "en": "Parts/Repair",
                "fr": "Pièces de rechange"
              }
            }
          ]
        },
        "article_sub_group": {
          "type": "codelist:article_sub_group",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "code": "2N01",
              "code_international": "2N01",
              "value": {
                "nl": "Standaarden",
                "en": "Kickstand",
                "fr": "Béquilles"
              }
            }
          ]
        },
        "keyword": {
          "type": "codelist:keyword",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "code": "STANDAARD",
              "code_international": "KICKSTAND",
              "value": {
                "nl": "Standaard",
                "en": "Kickstand",
                "fr": "Standard"
              }
            }
          ]
        },
        "model": {
          "type": "localized-strings",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "value": {
                "nl": "JUMBO"
              }
            }
          ]
        },
        "image_url": {
          "type": "string[]",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "value": [
                "http://www.accentry.com/upload/Juncker/680862.JPG"
              ]
            }
          ]
        },
        "basic_color": {
          "type": "codelist:base_color",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "code": "ZWART",
              "code_international": "BLACK",
              "value": {
                "nl": "Zwart",
                "en": "Black",
                "fr": "Noir"
              }
            }
          ]
        },
        "color_description": {
          "type": "localized-strings",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "value": {
                "nl": "ZWART"
              }
            }
          ]
        },
        "description": {
          "type": "string",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "value": {
                "nl": "STANDAARD URSUS 26 JUMBO TWEEPOOT ZWART"
              }
            }
          ]
        },
        "long_description": {
          "type": "localized-strings",
          "values": [
            {
              "supplier_ids": [
                5229
              ],
              "value": {
                "nl": "STANDAARD URSUS 26 JUMBO TWEEPOOT ZWART"
              }
            }
          ]
        }
      }
    }
  ],
  "pagination": {
    "next_url": "https://s01.cyclesoftware.nl/api/v4/articledata/entries.json?token=ABC"
  }
}
```

## Data-types - V4

Every property has it's own value structure. See the properties endpoint for example values.

| Data-type                        | Description                                                                           |
|----------------------------------|---------------------------------------------------------------------------------------|
| `codelist:article_group`         | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/article_group.json`         |
| `codelist:article_main_group`    | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/article_main_group.json`    |
| `codelist:article_sub_group`     | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/article_sub_group.json`     |
| `codelist:base_color`            | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/base_color.json`            |
| `codelist:battery_position`      | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/battery_position.json`      |
| `codelist:battery_type`          | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/battery_type.json`          |
| `codelist:brake_system`          | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/brake_system.json`          |
| `codelist:brand`                 | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/brand.json`                 |
| `codelist:customer_group`        | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/customer_group.json`        |
| `codelist:display_handling`      | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/display_handling.json`      |
| `codelist:display_type`          | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/display_type.json`          |
| `codelist:ebike_system`          | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/ebike_system.json`          |
| `codelist:electric_bicycle_type` | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/electric_bicycle_type.json` |
| `codelist:etrto_wheelsize`       | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/etrto_wheelsize.json`       |
| `codelist:frame`                 | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/frame.json`                 |
| `codelist:frame_material`        | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/frame_material.json`        |
| `codelist:function`              | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/function.json`              |
| `codelist:gear_system`           | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/gear_system.json`           |
| `codelist:keyword`               | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/keyword.json`               |
| `codelist:moped_category`        | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/moped_category.json`        |
| `codelist:moped_engine`          | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/moped_engine.json`          |
| `codelist:moped_transmission`    | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/moped_transmission.json`    |
| `codelist:motor_position`        | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/motor_position.json`        |
| `codelist:position`              | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/position.json`              |
| `codelist:qualitymark`           | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/qualitymark.json`           |
| `codelist:sensor_type[]`         | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/sensor_type.json`           |
| `codelist:status`                | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/status.json`                |
| `codelist:supplier`              | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/supplier.json`              |
| `codelist:surcharge`             | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/surcharge.json`             |
| `codelist:vat`                   | `https://api.cyclesoftware.nl/api/v4/articledata/codelist/vat.json`                   |
| `boolean`                        | Boolean value                                                                         |
| `date`                           | Date (Y-m-d)                                                                          |
| `decimal`                        | Decimal or float value                                                                |
| `integer`                        | Integer value                                                                         |
| `localized-strings`              | Localized string object                                                               |
| `object[]`                       | List of objects                                                                       |
| `string`                         | String value                                                                          |
| `string[]`                       | List of strings                                                                       |
| `image[]`                        | List of images                                                                        |
| `battery[]`                      | List of battery options                                                               |
| `document[]`                     | List of documents                                                                     |
| `bundle[]`                       | List of product bundles                                                               |

### Localized-strings type ###

```json
{
  "user": "User defined description",
  "nl": "Description in Dutch",
  "en": "Description in English",
  "fr": "Description in French"
}
```

This object provides translations for a description in the available languages. If a language is not available the key
is omitted from the body.

| Property | Type     | Nullable | Description                                                                                                |
|----------|----------|----------|------------------------------------------------------------------------------------------------------------|
| `user`   | `string` | `true`   | The user defined description e.g. `User defined description` (primarily used when language code is unsure) |
| `nl`     | `string` | `true`   | The description for language code `nl` e.g. `Description in Dutch`                                         |
| `en`     | `string` | `true`   | The description for language code `en` e.g. `Description in English`                                       |
| `fr`     | `string` | `true`   | The description for language code `fr` e.g. `Description in French`                                        |

### Image type ###

```json
{
  "date_modified": "2012-05-08 08:02:58",
  "url_thumb": "https://cdn.cyclesoftware.nl/app/img/Y/artPic_public_T_18563.jpg",
  "url_large": "https://cdn.cyclesoftware.nl/app/img/Y/artPic_public_L_18563.jpg"
}
```

| Property        | Type       | Description                                                                                |
|-----------------|------------|--------------------------------------------------------------------------------------------|
| `date_modified` | `datetime` | Modification datetime e.g. `2012-05-08 08:02:58`                                           |
| `url_thumb`     | `string`   | URL to thumb image e.g. `https://cdn.cyclesoftware.nl/app/img/Y/artPic_public_T_18563.jpg` |
| `url_large`     | `string`   | URL to large image e.g. `https://cdn.cyclesoftware.nl/app/img/Y/artPic_public_L_18563.jpg` |

### Battery type ###

```json
{
  "battery_additional_costs": 200,
  "battery_ampere_hour": 1,
  "battery_brand": "BOSCH",
  "battery_capacity": 400,
  "battery_chargeable_in_bike": false,
  "battery_fast_recharge_time": 2,
  "battery_included_in_base_price": false,
  "battery_location": "FRAME",
  "battery_model": "Model name 1",
  "battery_ranges": [
    {
      "range_avg": 50,
      "range_description": "Fast",
      "range_max": 100,
      "range_min": 10
    },
    {
      "range_avg": 30,
      "range_description": "Medium",
      "range_max": 150,
      "range_min": 75
    }
  ],
  "battery_recharge_time": 3,
  "battery_removeable": true,
  "battery_type": "LI-ION",
  "battery_voltage": 20,
  "battery_weight": 5
}
```

| Property                             | Type      | Omittable | Description                                                                 |
|--------------------------------------|-----------|-----------|-----------------------------------------------------------------------------|
| `battery_additional_costs`           | `integer` | `true`    | Additional costs against retail price e.g. `200`                            |
| `battery_ampere_hour`                | `integer` | `true`    | Battery ampére e.g. `20`                                                    |
| `battery_brand`                      | `string`  | `true`    | Brand name of battery e.g. `BOSCH`                                          |
| `battery_capacity`                   | `integer` | `true`    | Capacity in `Wh` e.g. `400`                                                 |
| `battery_chargeable_in_bike`         | `boolean` | `true`    | `true` if you can charge in the bike e.g. `false`                           |
| `battery_fast_recharge_time`         | `integer` | `true`    | Time in hours to recharche in fast mode e.g. `2`                            |
| `battery_recharge_time`              | `integer` | `true`    | Default recharche time e.g. `3` hours                                       |
| `battery_included_in_base_price`     | `boolean` | `true`    | Wether the price of this option is included in the retail price e.g. `true` |
| `battery_location`                   | `string`  | `true`    | Location see `codelist:battery_position` e.g. `FRAME`                       |
| `battery_model`                      | `string`  | `true`    | The model description of battery e.g. `Model name 1`                        |
| `battery_ranges`                     | `array`   | `true`    | List of ranges for different modes                                          |
| `battery_ranges[].range_avg`         | `integer` | `true`    | Average range in `km` e.g. `50`                                             |
| `battery_ranges[].range_description` | `string`  | `true`    | e.g. `Fast`                                                                 |
| `battery_ranges[].range_max`         | `integer` | `true`    | Maximum range in `km`e.g. `100`                                             |
| `battery_ranges[].range_min`         | `integer` | `true`    | Minimal range in `km`e.g. `10`                                              |
| `battery_removeable`                 | `boolean` | `true`    | `true` if you can demount the battery from bike e.g. `true`                 |
| `battery_type`                       | `string`  | `true`    | Battery type see code list `codelist:battery_type` e.g. `LI-ION`            |
| `battery_voltage`                    | `integer` | `true`    | Voltage of battery e.g. `20`                                                |
| `battery_weight`                     | `integer` | `true`    | Weight in `kg` e.g. `5`                                                     |

### Document type ###

```json
{
  "url": "https://url.to.guid",
  "type": "USER GUIDE"
}
```

Refers to a document with documentation

| Property | Type     | Description                                |
|----------|----------|--------------------------------------------|
| `url`    | `string` | URL to document e.g. `https://url.to.guid` |
| `type`   | `string` | Type e.g. `USER GUIDE`                     |

## Properties - V4 ##

Get definition of properties with types and examples.

| Property                              | Type               | Description                                                                                                                         |
|---------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| `error`                               | `boolean`          | `true` if an error occurred                                                                                                         |
| `error_message`                       | `?string`          | Error message if occurred                                                                                                           |
| `data<:property_name>.property_id`    | `integer`          | ID of property e.g. `310`                                                                                                           |
| `data<:property_name>.property_name`  | `string`           | Property definition e.g. `article_main_group`                                                                                       |
| `data<:property_name>.data_type`      | `string`           | Data type e.g. `boolean`, `integer`, or referring to codelist`codelist:article_main_group`                                          |
| `data<:property_name>.unit`           | `?string`          | Unit e.g. `cm`, `kg` or `null` if no unit applicable                                                                                |
| `data<:property_name>.description`    | `localized-string` | Object with localized descriptions of property                                                                                      |
| `data<:property_name>.description.nl` | `string`           | e.g. `Hoofdgroep`                                                                                                                   |
| `data<:property_name>.description.en` | `string`           | e.g. `Main group`                                                                                                                   |
| `data<:property_name>.description.fr` | `string`           | e.g. `Groupe principal`                                                                                                             |
| `data<:property_name>.example_value`  | `mixed`            | An example value found in article data endpoint. e.g. `1` or an object                                                              |
| `data<:property_name>.code_list`      | `?string`          | If codelist associated the URL to code list e.g. `https://s01.cyclesoftware.nl/api/v4/articledata/codelist/article_main_group.json` |

> HTTP Request

```http
GET /api/v4/articledata/properties.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```json
{
  "error": false,
  "error_message": null,
  "data": {
    "article_main_group": {
      "property_id": 310,
      "property_name": "article_main_group",
      "data_type": "codelist:article_main_group",
      "unit": null,
      "description": {
        "nl": "Hoofdgroep",
        "en": "Main group",
        "fr": "Groupe principal"
      },
      "example_value": "1",
      "code_list": "https://s01.cyclesoftware.nl/api/v4/articledata/codelist/article_main_group.json"
    },
    "handle_operation": {
      "property_id": 114,
      "property_name": "handle_operation",
      "data_type": "boolean",
      "unit": null,
      "description": {
        "nl": "Handvatbediening",
        "en": "Handle operation",
        "fr": "Fonctionnement de la poignée"
      },
      "example_value": true
    },
    "model_year": {
      "property_id": 120,
      "property_name": "model_year",
      "data_type": "integer",
      "unit": null,
      "description": {
        "nl": "Modeljaar",
        "en": "Model year",
        "fr": "Année modèle"
      },
      "example_value": 2024
    },
    "highres_image_url": {
      "property_id": 133,
      "property_name": "highres_image_url",
      "data_type": "string[]",
      "unit": null,
      "description": {
        "nl": "High resolution afbeelding URL",
        "en": "Highres image URL",
        "fr": "URL de l'image haute résolution"
      },
      "example_value": [
        "http://meridaxtraazz.nl/bikeimages/merida/2013/2048/3140.jpg"
      ]
    },
    "weight_bruto": {
      "property_id": 36,
      "property_name": "weight_bruto",
      "data_type": "decimal",
      "unit": "kg",
      "description": {
        "nl": "Bruto gewicht",
        "en": "Gross weight",
        "fr": "Poids brut"
      },
      "example_value": 10
    },
    "pos_description": {
      "property_id": 142,
      "property_name": "pos_description",
      "data_type": "string",
      "unit": null,
      "description": {
        "nl": "Kassabontekst",
        "en": "Receipt text",
        "fr": "Texte du reçu"
      },
      "example_value": {
        "user": "Kassabontekst stored in account",
        "nl": "Omschrijving - Kassabontekst",
        "en": "Description - Receipt text",
        "fr": "Description - Texte du reçu"
      }
    }
  }
}
```

## Code lists - V4 ##

Get code list entries.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v4/articledata/codelist/:name.json</h6>
	</div>
</div>

### URL parameters ###

| Property | Type     | Description               |
|----------|----------|---------------------------|
| `name`   | `string` | The name of the code list |


### Properties ###

| Property                    | Type               |     | Description                              |
|-----------------------------|--------------------|:----|------------------------------------------|
| `error`                     | `boolean`          |     | `true` if an error occurred e.g. `false` |
| `error_message`             | `?string`          |     | Error message if available               |
| `data`                      | `object[]`         |     | List of code list entries                |
| `data[].code`               | `string`           |     | Code value e.g. `2A`                     |
| `data[].code_international` | `string`           |     | International code value e.g. `BLACK`    |
| `data[].codelist`           | `string`           |     | e.g. `codelist:name-of-list`             |
| `data[].description`        | `localized-string` |     | Object with localized descriptions       |
| `data[].description.de`     | `string`           |     | e.g. `Description in German`             |
| `data[].description.en`     | `string`           |     | e.g. `Description in English`            |
| `data[].description.fr`     | `string`           |     | e.g. `Description in French`             |
| `data[].description.nl`     | `string`           |     | e.g. `Description in Dutch`              |

> HTTP Request

```http
GET /api/v4/articledata/codelist/article_main_group.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response

```json
{
  "error": false,
  "error_message": null,
  "data": [
    {
      "codelist": "codelist:article_main_group",
      "code": "1",
      "code_international": "1",
      "description": {
        "nl": "Fietsen",
        "fr": "Vélos",
        "en": "Bikes",
        "de": "Radfahren"
      }
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "2",
      "code_international": "2",
      "description": {
        "nl": "O&A",
        "fr": "Pièces et accessoires",
        "en": "Parts and accessories",
        "de": "Teile und Zubehör"
      }
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "3",
      "code_international": "3",
      "description": {
        "nl": "Kleding",
        "fr": "Vêtements",
        "en": "Clothing",
        "de": "Kleidung"
      }
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "4",
      "code_international": "4",
      "description": {
        "nl": "Fitness",
        "fr": "Fitness",
        "en": "Fitness",
        "de": "Fitness"
      }
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "5",
      "code_international": "5",
      "description": {
        "nl": "Occasions/Doorlevering",
        "fr": "Occasions / Livraison",
        "en": "Second hand / b2b sales",
        "de": "Anlässe / Lieferung"
      }
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "6",
      "code_international": "6",
      "description": {
        "nl": "Overigen",
        "fr": "Autres",
        "en": "Miscellaneous",
        "de": "Andere"
      }
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "7",
      "code_international": "7",
      "description": {
        "nl": "Bromfietsen",
        "fr": "Cyclomoteurs",
        "en": "Mopeds",
        "de": "Mopeds"
      }
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "8",
      "code_international": "8",
      "description": {
        "nl": "Bromfietsonderdelen",
        "fr": "Pièces de cyclomoteur",
        "en": "Moped parts",
        "de": "Moped Teile"
      }
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "9",
      "code_international": "9",
      "description": {
        "nl": "Tarieven",
        "fr": "Tarifs",
        "en": "Rates",
        "de": "Preise"
      }
    }
  ]
}
```

## Code list categories - V4 ##

Get code list for article groups / categories.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/api/v4/articledata/codelist/tree/:type.json</h6>
	</div>
</div>

### URL parameters ###

| Property | Type     | Description                                 |
|----------|----------|---------------------------------------------|
| `type`   | `string` | `bikes`, `articles` or `all-article-groups` |

### Properties ###

| Property                    | Type               | Description                              |
|-----------------------------|--------------------|------------------------------------------|
| `error`                     | `boolean`          | `true` if an error occurred e.g. `false` |
| `error_message`             | `?string`          | Error message if available               |
| `data`                      | `object[]`         | List of code list entries                |
| `data[].code`               | `string`           | Code value e.g. `2A`                     |
| `data[].code_international` | `string`           | International code value e.g. `BLACK`    |
| `data[].codelist`           | `string`           | e.g. `codelist:name-of-list`             |
| `data[].description`        | `localized-string` | Object with localized descriptions       |
| `data[].description.de`     | `string`           | e.g. `Description in German`             |
| `data[].description.en`     | `string`           | e.g. `Description in English`            |
| `data[].description.fr`     | `string`           | e.g. `Description in French`             |
| `data[].description.nl`     | `string`           | e.g. `Description in Dutch`              |
| `data[].sub_options`        | `object[]`         | Sub groups                               |

> HTTP Request

```http
GET /api/v4/articledata/codelist/tree/all-article-groups.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Accept: application/json
```

> HTTP Response (partial)

```json
{
  "error": false,
  "error_message": null,
  "data": [
    {
      "property": "article_main_group",
      "code": "1",
      "code_international": "1",
      "description": {
        "nl": "Fietsen",
        "fr": "Vélos",
        "en": "Bikes",
        "de": "Radfahren"
      },
      "sub_options": [
        {
          "property": "article_sub_group",
          "code": "A",
          "code_international": "A",
          "description": {
            "nl": "Stadsfietsen",
            "fr": "Vélos De Ville",
            "en": "Citybike",
            "de": "City-Bike"
          },
          "sub_options": [
            {
              "property": "article_sub_group",
              "code": "0",
              "code_international": "0",
              "description": {
                "nl": "Stadsfiets",
                "fr": "Vélo de Ville",
                "en": "City bike without gear or with hub gear",
                "de": "City-Bike ohne Kettenschaltung oder Nabenschaltung"
              }
            },
            {
              "property": "article_sub_group",
              "code": "1",
              "code_international": "1",
              "description": {
                "nl": "Stadsfiets (elektrisch)",
                "fr": "Vélo de Ville (électrique)",
                "en": "E-bike city bike without gear system or with hub gear",
                "de": "Elektrisches Citybike ohne Kettenschaltung oder Nabenschaltung"
              }
            },
            {
              "property": "article_sub_group",
              "code": "10",
              "code_international": "10",
              "description": {
                "nl": "Transportfiets",
                "fr": "Vélo de transport",
                "en": "Transport bike without gear system or with hub gear",
                "de": "Transport fahrräder ohne Kettenschaltung oder Nabenschaltung"
              }
            },
            {
              "property": "article_sub_group",
              "code": "11",
              "code_international": "11",
              "description": {
                "nl": "Transportfiets (elektrisch)",
                "fr": "Vélo de transport (électrique)",
                "en": "Transport e-bike without gear or with hub gear",
                "de": "E-bike transport fahrräd ohne Kettenschaltung oder Nabenschaltung"
              }
            },
            {
              "property": "article_sub_group",
              "code": "20",
              "code_international": "20",
              "description": {
                "nl": "Familie fiets",
                "fr": "Vélo familial",
                "en": "Family bike without gear or with hub gear",
                "de": "Familien Fahräd ohne Kettenschaltung oder Nabenschaltung"
              }
            },
            {
              "property": "article_sub_group",
              "code": "21",
              "code_international": "21",
              "description": {
                "nl": "Familie fiets (elektrisch)",
                "fr": "Vélo familial (électrique)",
                "en": "Family e-bike without gear or with hub gear",
                "de": "E-bike Familien Fahräd ohne Kettenschaltung oder Nabenschaltung"
              }
            }
          ]
        },
        {
          "property": "article_sub_group",
          "code": "B",
          "code_international": "B",
          "description": {
            "nl": "Hybride fietsen",
            "fr": "VTC",
            "en": "Hybrid bikes",
            "de": "Hybrid Fahrrad"
          },
          "sub_options": [
            {
              "property": "article_sub_group",
              "code": "0",
              "code_international": "0",
              "description": {
                "nl": "Hybride fiets",
                "fr": "Vélo Hybride",
                "en": "Hybrid bike with derailleur gears",
                "de": "Hybrid-Fahrrad mit Kettenschaltung"
              }
            },
            {
              "property": "article_sub_group",
              "code": "1",
              "code_international": "1",
              "description": {
                "nl": "Hybride fiets (elektrisch)",
                "fr": "Vélos Hybrides Electriques",
                "en": "E-bike Hybrid bike with derailleur gears",
                "de": "E-Bike Hybrid -Bike mit Kettenschaltung"
              }
            }
          ]
        }
      ]
    }
  ]
}

```


## Article batch updates ##

Apply batch updates to articles.

***Authentication mechanism***

- Basic HTTP Authentication
- Scopes: `resources`

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">PATCH</i>
		<h6>/api/v1/articles/batch/update.json</h6>
	</div>
</div>

### Request properties

| Property                                | Type       | Required | Description                                                                                                                                                  |
|-----------------------------------------|------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `updates`                               | `object[]` | `true`   | Array with data objects, maximum of 150 items                                                                                                                |
| `updates[].barcode`                     | `string`   | `true`   | Barcode of the article e.g. `878825512152`                                                                                                                   |
| `updates[].update_mode`                 | `string`   | `false`  | Update mode e.g. `update_or_create`, `update_only`, `create_only`, `delete_if_no_stock`                                                                      |
| `updates[].pos_group_id`                | `integer`  | `false`  | POS group ID e.g. `5` see `pos_groups`. See `/api/v1/common/enum/pos-groups.json`                                                                            |
| `updates[].article_main_group`          | `integer`  | `false`  | Main article group ID e.g. `2` if provided `article_group` and `article_sub_group` are also required. See `/api/v4/articledata/codelist/tree/articles.json`  |
| `updates[].article_group`               | `string`   | `false`  | Article group ID e.g. `A`  if provided `article_main_group` and `article_sub_group` are also required. See `/api/v4/articledata/codelist/tree/articles.json` |
| `updates[].article_sub_group`           | `integer`  | `false`  | Sub article group ID e.g. `2`  if provided `article_main_group` and `article_group` are also required. See `/api/v4/articledata/codelist/tree/articles.json` |
| `updates[].brand_name`                  | `string`   | `false`  | Brand name e.g. `SCHWALBE` (advice to use `/api/v4/articledata/codelist/brand.json`)                                                                         |
| `updates[].custom_variable_1`           | `string`   | `false`  | Custom variable 1 e.g. `Some Value`                                                                                                                          |
| `updates[].custom_variable_2`           | `string`   | `false`  | Custom variable 2 e.g. `Some Value`                                                                                                                          |
| `updates[].custom_variable_3`           | `string`   | `false`  | Custom variable 3 e.g. `Some Value`                                                                                                                          |
| `updates[].custom_variable_4`           | `string`   | `false`  | Custom variable 4 e.g. `Some Value`                                                                                                                          |
| `updates[].custom_variable_5`           | `string`   | `false`  | Custom variable 5 e.g. `Some Value`                                                                                                                          |
| `updates[].custom_variable_6`           | `string`   | `false`  | Custom variable 6 e.g. `Some Value`                                                                                                                          |
| `updates[].description_en`              | `string`   | `false`  | Description in English e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                                                        |
| `updates[].description_nl`              | `string`   | `false`  | Description in Dutch (generally default description) e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                          |
| `updates[].description_fr`              | `string`   | `false`  | Description in French e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                                                         |
| `updates[].ecommerce`                   | `boolean`  | `false`  | Available for e-commerce e.g. `false`                                                                                                                        |
| `updates[].ecommerce_price_cents`       | `integer`  | `false`  | The e-commerce price in cents e.g. `6290`                                                                                                                    |
| `updates[].ecommerce_promo_price_cents` | `integer`  | `false`  | The e-commerce promo price in cents e.g. `0` (disabled if `0`)                                                                                               |
| `updates[].ecommerce_promo_price_from`  | `?date`    | `false`  | The date for e-commerce promo price interval start e.g. `2022-01-01` or `null`                                                                               |
| `updates[].ecommerce_promo_price_until` | `?date`    | `false`  | The date for e-commerce promo price interval until e.g. `2022-01-01` or `null`                                                                               |
| `updates[].min_stock`                   | `integer`  | `false`  | Minimal stock level e.g. `10`                                                                                                                                |
| `updates[].max_stock`                   | `integer`  | `false`  | Maximum stock level e.g. `20`                                                                                                                                |
| `updates[].stock`                       | `integer`  | `false`  | Stock level e.g. `1`. You can not update the stock if stock is already non-zero.                                                                             |
| `updates[].pos_promo_price_cents`       | `integer`  | `false`  | Promo price in cents e.g. `5750` (disabled if `0`)                                                                                                           |
| `updates[].pos_promo_price_from`        | `?date`    | `false`  | The date for promo price interval start e.g. `2022-01-01` or `null`                                                                                          |
| `updates[].pos_promo_price_until`       | `?date`    | `false`  | The date for promo price interval until e.g. `2022-01-01` or `null`                                                                                          |
| `updates[].pos_sales_price_cents`       | `integer`  | `false`  | The POS sales price in cents e.g. `6290`                                                                                                                     |
| `updates[].purchase_price_cents`        | `integer`  | `false`  | The purchase price in cents e.g. `3624`                                                                                                                      |


### Result properties

| Property                                        | Type       | Nullable | Omittable | Description                                                                                                                                                                                                                                                                                 |
|-------------------------------------------------|------------|----------|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `results`                                       | `object[]` | `false`  |           | List of objects                                                                                                                                                                                                                                                                             |
| `results[].barcode`                             | `string`   | `false`  |           | Barcode of the article e.g. `878825512152`                                                                                                                                                                                                                                                  |
| `results[].result`                              | `string`   | `false`  |           | `success` (all fields updated),  <br/>`partial` (not all fields could be updated see `results[].skipped_fields` <br/>`success_with_warnings` (all fields updated with some warnings, see `results[].warnings`) <br/>`error` (article not updated or created, see `results[].error.message`) |
| `results[].article`                             | `object`   | `false`  | `Yes`     | Object with resulting article details, omitted when an error occurs or when deleted and no information available                                                                                                                                                                            |
| `results[].article.barcode`                     | `string`   | `false`  |           | Barcode of the article e.g. `878825512152`                                                                                                                                                                                                                                                  |
| `results[].article.store_id`                    | `integer`  | `false`  |           | Store ID related to `stock`, `min_stock`, and `max_stock` e.g. `1`                                                                                                                                                                                                                          |
| `results[].article.update_mode`                 | `string`   | `false`  |           | Update mode e.g. `update_or_create`, `update_only`, `create_only`                                                                                                                                                                                                                           |
| `results[].article.pos_group_id`                | `integer`  | `false`  |           | POS group ID e.g. `5` see `pos_groups` (see code list `/api/v1/common/enum/pos-groups.json`)                                                                                                                                                                                                |
| `results[].article.article_main_group`          | `integer`  | `false`  |           | Main article group ID e.g. `2`  (see code list `/api/v4/articledata/codelist/tree/articles.json`)                                                                                                                                                                                           |
| `results[].article.article_group`               | `string`   | `false`  |           | Article group ID e.g. `A`  (see code list `/api/v4/articledata/codelist/tree/articles.json`)                                                                                                                                                                                                |
| `results[].article.article_sub_group`           | `integer`  | `false`  |           | Sub article group ID e.g. `2`  (see code list `/api/v4/articledata/codelist/tree/articles.json`)                                                                                                                                                                                            |
| `results[].article.brand_name`                  | `string`   | `false`  |           | Brand name e.g. `SCHWALBE` (advice to use `/api/v4/articledata/codelist/brand.json`)                                                                                                                                                                                                        |
| `results[].article.currency`                    | `string`   | `false`  |           | Currency `EUR`                                                                                                                                                                                                                                                                              |
| `results[].article.custom_variable_1`           | `string`   | `false`  |           | Custom variable 1 e.g. `Some Value`                                                                                                                                                                                                                                                         |
| `results[].article.custom_variable_2`           | `string`   | `false`  |           | Custom variable 2 e.g. `Some Value`                                                                                                                                                                                                                                                         |
| `results[].article.custom_variable_3`           | `string`   | `false`  |           | Custom variable 3 e.g. `Some Value`                                                                                                                                                                                                                                                         |
| `results[].article.custom_variable_4`           | `string`   | `false`  |           | Custom variable 4 e.g. `Some Value`                                                                                                                                                                                                                                                         |
| `results[].article.custom_variable_5`           | `string`   | `false`  |           | Custom variable 5 e.g. `Some Value`                                                                                                                                                                                                                                                         |
| `results[].article.custom_variable_6`           | `string`   | `false`  |           | Custom variable 6 e.g. `Some Value`                                                                                                                                                                                                                                                         |
| `results[].article.description_en`              | `string`   | `false`  |           | Description in English e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                                                                                                                                                                                       |
| `results[].article.description_nl`              | `string`   | `false`  |           | Description in Dutch (generally default description) e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                                                                                                                                                         |
| `results[].article.description_fr`              | `string`   | `false`  |           | Description in French e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                                                                                                                                                                                        |
| `results[].article.ecommerce`                   | `boolean`  | `false`  |           | Available for e-commerce e.g. `false`                                                                                                                                                                                                                                                       |
| `results[].article.ecommerce_price_cents`       | `integer`  | `false`  |           | The e-commerce price in cents e.g. `6290`                                                                                                                                                                                                                                                   |
| `results[].article.ecommerce_promo_price_cents` | `integer`  | `false`  |           | The e-commerce promo price in cents e.g. `0` (disabled if `0`)                                                                                                                                                                                                                              |
| `results[].article.ecommerce_promo_price_from`  | `date`     | `true`   |           | The date for e-commerce promo price interval start e.g. `2022-01-01`                                                                                                                                                                                                                        |
| `results[].article.ecommerce_promo_price_until` | `date`     | `true`   |           | The date for e-commerce promo price interval until e.g. `2022-01-01`                                                                                                                                                                                                                        |
| `results[].article.min_stock`                   | `integer`  | `false`  |           | Minimal stock level e.g. `10`                                                                                                                                                                                                                                                               |
| `results[].article.max_stock`                   | `integer`  | `false`  |           | Maximum stock level e.g. `20`                                                                                                                                                                                                                                                               |
| `results[].article.stock`                       | `integer`  | `false`  |           | Stock level e.g. `1`                                                                                                                                                                                                                                                                        |
| `results[].article.pos_promo_price_cents`       | `integer`  | `false`  |           | Promo price in cents e.g. `5750` (disabled if `0`)                                                                                                                                                                                                                                          |
| `results[].article.pos_promo_price_from`        | `date`     | `true`   |           | The date for promo price interval start e.g. `2022-01-01`                                                                                                                                                                                                                                   |
| `results[].article.pos_promo_price_until`       | `date`     | `true`   |           | The date for promo price interval until e.g. `2022-01-01`                                                                                                                                                                                                                                   |
| `results[].article.pos_sales_price_cents`       | `integer`  | `false`  |           | The POS sales price in cents e.g. `6290`                                                                                                                                                                                                                                                    |
| `results[].article.purchase_price_cents`        | `integer`  | `false`  |           | The purchase price in cents e.g. `3624`                                                                                                                                                                                                                                                     |
| `results[].skipped_fields`                      | `string[]` | `false`  | `Yes`     | List of fields which are ignored in the update. Omitted if not present                                                                                                                                                                                                                      |
| `results[].warnings`                            | `object[]` | `false`  | `Yes`     | List of warnings, omitted if status `error` or `success`                                                                                                                                                                                                                                    |
| `results[].warnings[].field`                    | `?string`  | `false`  |           | The field which the warning is related to if applicable e.g. `ecommerce_price_cents`                                                                                                                                                                                                        |
| `results[].warnings[].message`                  | `string`   | `false`  |           | The warning message                                                                                                                                                                                                                                                                         |
| `results[].warnings[].code_list`                | `string`   | `false`  | `Yes`     | The URL the the codelist if this applies to the `field` e.g. `https://s01.cyclesoftware.nl/api/v4/articledata/codelist/tree/articles.json`                                                                                                                                                  |
| `results[].error`                               | `object`   | `false`  | `Yes`     | Object with error info. Only present when status `error`                                                                                                                                                                                                                                    |
| `results[].error.message`                       | `string`   | `false`  |           | The error message in your locale e.g. `Maximaal 150 updates toegestaan per aanvraag`                                                                                                                                                                                                        |


> HTTP request

```http
PATCH /api/v1/articles/batch/update.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
Content-type: application/json
Accept: application/json

{
    "updates": [
        {
            "barcode": "4026495856010",
            "brand_name": "SCHWALBE",
            "description_nl": "##28x1 1/2 (40-635) Delta Cruiser Plus naturel RS Flamand",
            "description_en": " ##28x1 1/2 (40-635) Delta Cruiser Plus natural RS Flamand",
            "description_fr": "##28x1 1/2 (40-635) Delta Cruiser Plus naturel RS French",
            "pos_group_id": 11,
            "article_main_group": 2,
            "article_group": "A",
            "article_sub_group": 2,
            "pos_sales_price_cents": 2490,
            "pos_promo_price_cents": 0,
            "pos_promo_price_from": null,
            "pos_promo_price_until": null,
            "purchase_price_cents": 100,
            "ecommerce": true,
            "ecommerce_price_cents": 2490,
            "ecommerce_promo_price_cents": 0,
            "ecommerce_promo_price_from": null,
            "ecommerce_promo_price_until": null,
            "stock": 20,
            "max_stock": 17,
            "min_stock": 13,
            "custom_variable_1": "Variable 1",
            "custom_variable_2": "Variable 2",
            "custom_variable_3": "Variable 3",
            "custom_variable_4": "Variable 4",
            "custom_variable_5": "Variable 5",
            "custom_variable_6": "Variable 6"
        },
        {
            "barcode": "4026495843614",
            "brand_name": "SCHWALBE",
            "description_nl": "##28x1 1/2 (40-635) Delta Cruiser Plus naturel RS Flamand 2",
            "pos_group_id": 11,
            "article_main_group": 2,
            "stock": 22,
            "max_stock": 17,
            "min_stock": 13
        },
        {
            "barcode": "4019238805475",
            "update_mode": "create_only",
            "brand_name": "SCHWALBE",
            "description_nl": "##28x1 1/2 (40-635) Delta Cruiser Plus naturel RS Flamand 2",
            "pos_group_id": 11,
            "stock": 22,
            "max_stock": 17,
            "min_stock": 13
        },
        {
            "barcode": "1121121222",
            "update_mode": "update_only",
            "brand_name": "SCHWALBE",
            "description_nl": "##28x1 1/2 (40-635) Delta Cruiser Plus naturel RS Flamand 2",
            "pos_group_id": 11,
            "stock": 22,
            "max_stock": 17,
            "min_stock": 13
        }
    ]
}
```

> HTTP Response

```http
HTTP/1.1 200 
Content-type: application/json; charset=utf-8
Content-length: 19744

{
    "results": [
        {
            "barcode": "4026495856010",
            "result": "success",
            "article": {
                "currency": "EUR",
                "store_id": 1,
                "barcode": "4026495856010",
                "brand_name": "SCHWALBE",
                "description_nl": "##28x1 1/2 (40-635) Delta Cruiser Plus naturel RS Flamand",
                "description_en": " ##28x1 1/2 (40-635) Delta Cruiser Plus natural RS Flamand",
                "description_fr": "##28x1 1/2 (40-635) Delta Cruiser Plus naturel RS French",
                "pos_group_id": 11,
                "article_main_group": 2,
                "article_group": "A",
                "article_sub_group": 2,
                "pos_sales_price_cents": 2490,
                "pos_promo_price_cents": 0,
                "pos_promo_price_from": null,
                "pos_promo_price_until": null,
                "purchase_price_cents": 100,
                "ecommerce": true,
                "ecommerce_price_cents": 2490,
                "ecommerce_promo_price_cents": 0,
                "ecommerce_promo_price_from": null,
                "ecommerce_promo_price_until": null,
                "stock": 20,
                "max_stock": 17,
                "min_stock": 13,
                "custom_variable_1": "Variable 1",
                "custom_variable_2": "Variable 2",
                "custom_variable_3": "Variable 3",
                "custom_variable_4": "Variable 4",
                "custom_variable_5": "Variable 5",
                "custom_variable_6": "Variable 6"
            }
        },
        {
            "barcode": "4026495843614",
            "result": "partial",
            "article": {
                "currency": "EUR",
                "store_id": 1,
                "barcode": "4026495843614",
                "brand_name": "SCHWALBE",
                "description_nl": "##28x1 1/2 (40-635) Delta Cruiser Plus naturel RS Flamand 2",
                "description_en": " ##28x1 1/2 (40-635) Delta Cruiser Plus natural RS Flamand",
                "description_fr": "##28x1 1/2 (40-635) Delta Cruiser Plus naturel RS French",
                "pos_group_id": 11,
                "article_main_group": 2,
                "article_group": "A",
                "article_sub_group": 2,
                "pos_sales_price_cents": 2490,
                "pos_promo_price_cents": 0,
                "pos_promo_price_from": null,
                "pos_promo_price_until": null,
                "purchase_price_cents": 100,
                "ecommerce": true,
                "ecommerce_price_cents": 2490,
                "ecommerce_promo_price_cents": 0,
                "ecommerce_promo_price_from": null,
                "ecommerce_promo_price_until": null,
                "stock": 20,
                "max_stock": 17,
                "min_stock": 13,
                "custom_variable_1": "",
                "custom_variable_2": "",
                "custom_variable_3": "",
                "custom_variable_4": "",
                "custom_variable_5": "",
                "custom_variable_6": ""
            },
            "skipped_fields": [
                "article_main_group",
                "stock"
            ],
            "warnings": [
                {
                    "field": "article_main_group",
                    "message": "article_main_group, article_group, article_sub_group zijn verplicht bij update van article_main_group",
                    "code_list": "https://api.cyclesoftware.nl/api/v4/articledata/codelist/tree/articles.json"
                },
                {
                    "field": "stock",
                    "message": "Je kunt de voorraad niet bijwerken wanneer deze niet gelijk is aan 0"
                }
            ]
        },
        {
            "barcode": "4019238805475",
            "result": "error",
            "error": {
                "message": "Dit artikel bestaat al."
            }
        },
        {
            "barcode": "1121121222",
            "result": "error",
            "error": {
                "message": "Article not found"
            }
        }
    ]
}

