# Article data #

The articledata APIs are designed for pulling article-information for e-commerce environments.

***Authentication***

- Basic HTTP Authentication
- Scope(s): `e-commerce`

## Articledata - V3 ##

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
is `/app/api/v3/articledata/750-750-0/`. If `next_resultset` is null no additional data is available.

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
  "next_resultset": "/app/api/v3/articledata/750-750-0/",
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
      "custom_variable_1": null,
      "custom_variable_2": null,
      "custom_variable_3": null,
      "custom_variable_4": null,
      "custom_variable_5": null,
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
      "custom_variable_1": null,
      "custom_variable_2": null,
      "custom_variable_3": null,
      "custom_variable_4": null,
      "custom_variable_5": null,
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
      "custom_variable_1": null,
      "custom_variable_2": null,
      "custom_variable_3": null,
      "custom_variable_4": null,
      "custom_variable_5": null,
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
| `lease_options`         | Array of objects with lease option                                                      |                                   |
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

| **Property**         | **Description**                                                                       | **Type**                                                         |
|----------------------|---------------------------------------------------------------------------------------|------------------------------------------------------------------|
| `type`               | b2b or b2c                                                                            | String                                                           |
| `platform`           | Name of the lease platform e.g. “cyclelease”                                          | String                                                           |
| `rrp`                | RRP used to calculate the fee                                                         | Decimal string                                                   |
| `duration_months`    | Contract length                                                                       | Integer                                                          |
| `fee_monthly_ex_vat` | The estimated base lease fee ex vat                                                   | Decimal string                                                   |
| `service`            | Services included                                                                     | Array of strings                                                 |
| `options`            | Additional selectable options with description and fee_monthly_ex_vat for each option | Array of object with elements description and fee_monthly_ex_vat |

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

This endpoint is currently in beta-phase. 

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

| GET parameter        | Type      | Description |
|----------------------|-----------|-------------|
| `:modified_since`    | `integer` |             |
| `:barcode`           | `barcode` |             |
| `:exclude_ecommerce` | `boolean` |             |
| `:exclude_articles`  | `boolean` |             |
| `:exclude_objects`   | `boolean` |             |
| `:per_store_id`      | `boolean` |             |

**Important***

- stock only present for non-objects
- objects lists the available stock objects

### Response properties ###

| Property                                                           | Type        | Omittable | Description                                                                                                                                |
|--------------------------------------------------------------------|-------------|-----------|--------------------------------------------------------------------------------------------------------------------------------------------|
| `data`                                                             | `object[]`  | `false`   |                                                                                                                                            |
| `data[].modified_at`                                               | `datetime`  | `false`   | Last modification of underlying data e.g. `2024-07-24 16:23:45`                                                                            |
| `data[].barcode`                                                   | `string`    | `false`   | The barcode of the article e.g. `5400928076890` (usually an EAN code)                                                                      |
| `data[].pricing`                                                   | `object`    | `false`   | Object with pricing information about the article`                                                                                         |
| `data[].pricing.currency`                                          | `string`    | `false`   | The currency code e.g. `EUR`                                                                                                               |
| `data[].pricing.rrp_cents`                                         | `integer`   | `false`   | Recommended retail price in cents e.g. `269900`                                                                                            |
| `data[].pricing.pos_sales_price_cents`                             | `integer`   | `false`   | POS sales price in cents e.g. `269900`                                                                                                     |
| `data[].pricing.ecommerce_price_cents`                             | `integer`   | `true`    | E-commerce sales price in cents e.g. `269900`                                                                                              |
| `data[].pricing.purchase_price_cents`                              | `integer`   | `true`    | Purchase price in cents (excluding VAT) e.g. `99500`                                                                                       |
| `data[].pricing.pos_group_id`                                      | `integer`   | `false`   | POS group ID e.g. `1` (see common enum)                                                                                                    |
| `data[].pricing.vat_code`                                          | `?integer`  | `true`    | VAT code if specified e.g. `2`, if no specified the default VAT-code of POS group is applied                                               |
| `data[].pricing.pos_promo_price_cents`                             | `?integer`  | `true`    | POS promo price in cents e.g. `4000`                                                                                                       |
| `data[].pricing.pos_promo_price_from`                              | `?date`     | `true`    | POS promo start date e.g. `2024-07-03`                                                                                                     |
| `data[].pricing.pos_promo_price_until`                             | `?date`     | `true`    | POS promo end date e.g. `2024-10-19`                                                                                                       |
| `data[].pricing.ecommerce_promo_price_cents`                       | `?integer`  | `true`    | E-commerce promo price in cents e.g. `3900`                                                                                                |
| `data[].pricing.ecommerce_promo_price_from`                        | `?date`     | `true`    | E-commerce promo start date e.g. `2024-07-01`                                                                                              |
| `data[].pricing.ecommerce_promo_price_until`                       | `?date`     | `true`    | E-commerce promo end date e.g. `2024-10-19`                                                                                                |
| `data[].objects`                                                   | `?object[]` | `false`   | When the article is an object (bicycle, moped) this element is present and contains unique objects                                         |
| `data[].objects[].object_code`                                     | `string`    | `false`   | e.g. `F.1-232432`                                                                                                                          |
| `data[].objects[].object_id`                                       | `integer`   | `false`   | e.g. `232432`                                                                                                                              |
| `data[].objects[].store_id`                                        | `integer`   | `false`   | e.g. `1`                                                                                                                                   |
| `data[].objects[].available`                                       | `boolean`   | `false`   | e.g. `true`                                                                                                                                |
| `data[].objects[].expected_at`                                     | `null`      | `true`    |                                                                                                                                            |
| `data[].objects[].is_demo`                                         | `boolean`   | `false`   | e.g. `false`                                                                                                                               |
| `data[].objects[].is_used`                                         | `boolean`   | `false`   | e.g. `false`                                                                                                                               |
| `data[].objects[].currency`                                        | `string`    | `false`   | e.g. `EUR`                                                                                                                                 |
| `data[].objects[].ecommerce_price_cents`                           | `integer`   | `false`   | e.g. `269900`                                                                                                                              |
| `data[].objects[].pos_sales_price_cents`                           | `integer`   | `false`   | e.g. `269900`                                                                                                                              |
| `data[].objects[].purchase_price_cents`                            | `integer`   | `false`   | e.g. `0`                                                                                                                                   |
| `data[].objects[].km_age`                                          | `null`      | `true`    |                                                                                                                                            |
| `data[].suppliers`                                                 | `object[]`  | `false`   | List of suppliers associated with the article                                                                                              |
| `data[].suppliers[]._id`                                           | `integer`   | `false`   | Internal ID e.g. `11043281`                                                                                                                |
| `data[].suppliers[].supplier_id`                                   | `integer`   | `false`   | Supplier ID e.g. `13005` (see common supplier list)                                                                                        |
| `data[].suppliers[].supplier_name`                                 | `string`    | `false`   | Supplier code name e.g. `BELGIAN CYCLING FACTORY`                                                                                          |
| `data[].suppliers[].article_id`                                    | `string`    | `false`   | Article number e.g. `SBIELARID023`                                                                                                         |
| `data[].suppliers[].model_id`                                      | `null`      | `true`    | Model ID, if other entries have the same model_id they could be grouped                                                                    |
| `data[].suppliers[].parent_barcode`                                | `null`      | `true`    | Parent barcode (if grouped within model_id)                                                                                                |
| `data[].suppliers[].currency`                                      | `string`    | `false`   | Currency code e.g. `EUR`                                                                                                                   |
| `data[].suppliers[].rrp_cents`                                     | `integer`   | `false`   | Recommended retail price in cents e.g. `269900`                                                                                            |
| `data[].suppliers[].purchase_price_cents`                          | `integer`   | `false`   | Purchase price in cents e.g. `0`                                                                                                           |
| `data[].suppliers[].package.package_contents`                      | `integer`   | `false`   | Number of consumer goods within delivery from supplier e.g. `1`                                                                            |
| `data[].suppliers[].package.min_order_quantity`                    | `integer`   | `false`   | Minimal order quantity for this supplier e.g. `1`                                                                                          |
| `data[].suppliers[].package.order_unit`                            | `integer`   | `false`   | Order unit for this supplier e.g. `1`                                                                                                      |
| `data[].properties<:property_name>.type`                           | `string`    | `false`   | The data type of the property e.g. `codelist:article_main_group` (see `Data-types` for possible types)                                     |
| `data[].properties<:property_name>.unit`                           | `?string`   | `true`    | The unit of data e.g. `kg` or `cm` if available.                                                                                           |
| `data[].properties<:property_name>.values`                         | `object[]`  | `false`   | Different values for the property                                                                                                          |
| `data[].properties<:property_name>.values[].supplier_ids`          | `integer[]` | `false`   | The list of supplier-ids which have this property in their article definition                                                              |
| `data[].properties<:property_name>.values[].object_ids`            | `array`     | `false`   | The list of object-ids which have this property in their definition                                                                        |
| `data[].properties<:property_name>.values[].code`                  | `?string`   | `true`    | If the data-type refers to a code list, this is the code value e.g. `1`                                                                    |
| `data[].properties<:property_name>.values[].code_international`    | `?string`   | `true`    | If the data-type refers to a code list, this is the international code value e.g. `1`                                                      |
| `data[].properties<:property_name>.values[].value.nl`              | `mixed`     | `false`   | Value will have the structure associated with the `type` .e.g `localized-string`, `string`, `decimal`                                      |
| `data[].properties<:property_name>.values[].value.en`              | `string`    | `false`   | e.g. `Bikes`                                                                                                                               |
| `data[].properties<:property_name>.values[].value.fr`              | `string`    | `false`   | e.g. `Vélos`                                                                                                                               |
| `data[].properties<:property_name>.values[].value.user`            | `string`    | `false`   | e.g. `Ridley Elykx A Black Powder Coating // Aluminium B`                                                                                  |
| `data[].properties<:property_name>.values[].value`                 | `array`     | `false`   | e.g. `2021`                                                                                                                                |
| `data[].properties<:property_name>.values[].value[]`               | `string`    | `false`   | e.g. `https://images.cyclingfactory.be/SBIELARID023_image_2048x.jpg`                                                                       |
| `data[].stock`                                                     | `?object`   | `false`   | Only present for non object entries, contains stock information within stores                                                              |
| `data[].stock.available`                                           | `boolean`   | `false`   | `true` if there is stock available within stores e.g. `false`                                                                              |
| `data[].stock.stores`                                              | `object`    | `false`   | Array with object information per store-id                                                                                                 |
| `data[].stock.stores[].store_id`                                   | `integer`   | `false`   | Store ID e.g. `1`                                                                                                                          |
| `data[].stock.stores[].stock_level`                                | `integer`   | `false`   | Stock level in this store e.g. `0`                                                                                                         |
| `data[].stock.stores[].locations`                                  | `array`     | `false`   | Stock locations associated with this article                                                                                               |
| `data[].stock.stores[].locations[].store_id`                       | `integer`   | `false`   | e.g. `1`                                                                                                                                   |
| `data[].stock.stores[].locations[].location_id`                    | `integer`   | `false`   | ID of the location e.g. `3`                                                                                                                |
| `data[].stock.stores[].locations[].location_x`                     | `integer`   | `false`   | Location x-axis e.g. `1`                                                                                                                   |
| `data[].stock.stores[].locations[].location_y`                     | `integer`   | `false`   | Location y-axis e.g. `2`                                                                                                                   |
| `data[].stock.stores[].locations[].location_capacity`              | `integer`   | `false`   | Capacity e.g. `33`                                                                                                                         |
| `data[].stock.stores[].locations[].location_bulk`                  | `string`    | `false`   | Bulk location name e.g. `Magazijn`                                                                                                         |
| `data[].properties<:property_name>.values[].value[].date_modified` | `datetime`  | `false`   | e.g. `2012-05-08 08:02:58`                                                                                                                 |
| `data[].properties<:property_name>.values[].value[].url_thumb`     | `string`    | `false`   | e.g. `https://cdn.cyclesoftware.nl/app/img/Y/artPic_public_T_18563.jpg`                                                                    |
| `data[].properties<:property_name>.values[].value[].url_large`     | `string`    | `false`   | e.g. `https://cdn.cyclesoftware.nl/app/img/Y/artPic_public_L_18563.jpg`                                                                    |
| `pagination.next_url`                                              | `?string`   | `true`    | If there is more data this is the URL to the next API request. `https://api.cyclesoftware.nl/api/v4/articledata/entries.json?token=abc...` |

### Data-types ###

Every property has it's own value structure. See the properties endpoint for example values.

| Data-type                                                                 | Description                                                                | Example |
|---------------------------------------------------------------------------|----------------------------------------------------------------------------|---------|
| `array[object(date_modified:datetime,url_large:string,url_thumb:string)]` | -                                                                          |
| `array[object(productbundle_contents:int,productbundle_item:string)]`     | -                                                                          |
| `array[object(url:string,type:string)]`                                   | -                                                                          |
| `codelist:article_group`                                                  | `https://api.cyclesoftware.nl/api/v4/codelists/article_group.json`         |
| `codelist:article_main_group`                                             | `https://api.cyclesoftware.nl/api/v4/codelists/article_main_group.json`    |
| `codelist:article_sub_group`                                              | `https://api.cyclesoftware.nl/api/v4/codelists/article_sub_group.json`     |
| `codelist:base_color`                                                     | `https://api.cyclesoftware.nl/api/v4/codelists/base_color.json`            |
| `codelist:battery_position`                                               | `https://api.cyclesoftware.nl/api/v4/codelists/battery_position.json`      |
| `codelist:battery_type`                                                   | `https://api.cyclesoftware.nl/api/v4/codelists/battery_type.json`          |
| `codelist:brake_system`                                                   | `https://api.cyclesoftware.nl/api/v4/codelists/brake_system.json`          |
| `codelist:brand`                                                          | `https://api.cyclesoftware.nl/api/v4/codelists/brand.json`                 |
| `codelist:customer_group`                                                 | `https://api.cyclesoftware.nl/api/v4/codelists/customer_group.json`        |
| `codelist:display_handling`                                               | `https://api.cyclesoftware.nl/api/v4/codelists/display_handling.json`      |
| `codelist:display_type`                                                   | `https://api.cyclesoftware.nl/api/v4/codelists/display_type.json`          |
| `codelist:ebike_system`                                                   | `https://api.cyclesoftware.nl/api/v4/codelists/ebike_system.json`          |
| `codelist:electric_bicycle_type`                                          | `https://api.cyclesoftware.nl/api/v4/codelists/electric_bicycle_type.json` |
| `codelist:etrto_wheelsize`                                                | `https://api.cyclesoftware.nl/api/v4/codelists/etrto_wheelsize.json`       |
| `codelist:frame`                                                          | `https://api.cyclesoftware.nl/api/v4/codelists/frame.json`                 |
| `codelist:frame_material`                                                 | `https://api.cyclesoftware.nl/api/v4/codelists/frame_material.json`        |
| `codelist:function`                                                       | `https://api.cyclesoftware.nl/api/v4/codelists/function.json`              |
| `codelist:gear_system`                                                    | `https://api.cyclesoftware.nl/api/v4/codelists/gear_system.json`           |
| `codelist:keyword`                                                        | `https://api.cyclesoftware.nl/api/v4/codelists/keyword.json`               |
| `codelist:moped_category`                                                 | `https://api.cyclesoftware.nl/api/v4/codelists/moped_category.json`        |
| `codelist:moped_engine`                                                   | `https://api.cyclesoftware.nl/api/v4/codelists/moped_engine.json`          |
| `codelist:moped_transmission`                                             | `https://api.cyclesoftware.nl/api/v4/codelists/moped_transmission.json`    |
| `codelist:motor_position`                                                 | `https://api.cyclesoftware.nl/api/v4/codelists/motor_position.json`        |
| `codelist:position`                                                       | `https://api.cyclesoftware.nl/api/v4/codelists/position.json`              |
| `codelist:qualitymark`                                                    | `https://api.cyclesoftware.nl/api/v4/codelists/qualitymark.json`           |
| `codelist:sensor_type[]`                                                  | `https://api.cyclesoftware.nl/api/v4/codelists/sensor_type.json`           |
| `codelist:status`                                                         | `https://api.cyclesoftware.nl/api/v4/codelists/status.json`                |
| `codelist:supplier`                                                       | `https://api.cyclesoftware.nl/api/v4/codelists/supplier.json`              |
| `codelist:surcharge`                                                      | `https://api.cyclesoftware.nl/api/v4/codelists/surcharge.json`             |
| `codelist:vat`                                                            | `https://api.cyclesoftware.nl/api/v4/codelists/vat.json`                   |
| `boolean`                                                                 | Boolean value                                                              |
| `date`                                                                    | Date (Y-m-d)                                                               |
| `decimal`                                                                 | Decimal or float value                                                     |
| `integer`                                                                 | Integer value                                                              |
| `localized-strings`                                                       | Localized string object                                                    |
| `object[]`                                                                | Array of objects                                                           |
| `string`                                                                  | String value                                                               |
| `string[]`                                                                | Array of strings                                                           |
| `image[]`                                                                 | Property `images`                                                          |
| `battery[]`                                                               | Property `images`                                                          |
| `document[]`                                                              | Property `images`                                                          |
| `bundle[]`                                                                | Property `images`                                                          |


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
}
```

## Properties - V4 ##

Get definition of properties with types and examples.

| Property                              | Type      | Description                                                                                                                         |
|---------------------------------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------|
| `error`                               | `boolean` | `true` if an error occurred                                                                                                         |
| `error_message`                       | `?string` | Error message if occurred                                                                                                           |
| `data<:property_name>.property_id`    | `integer` | ID of property e.g. `310`                                                                                                           |
| `data<:property_name>.property_name`  | `string`  | Property definition e.g. `article_main_group`                                                                                       |
| `data<:property_name>.data_type`      | `string`  | Data type e.g. `boolean`, `integer`, or referring to codelist`codelist:article_main_group`                                          |
| `data<:property_name>.unit`           | `?string` | Unit e.g. `cm`, `kg` or `null` if no unit applicable                                                                                |
| `data<:property_name>.description`    | `object`  | Object with localized descriptions of property                                                                                      |
| `data<:property_name>.description.nl` | `string`  | e.g. `Hoofdgroep`                                                                                                                   |
| `data<:property_name>.description.en` | `string`  | e.g. `Main group`                                                                                                                   |
| `data<:property_name>.description.fr` | `string`  | e.g. `Groupe principal`                                                                                                             |
| `data<:property_name>.example_value`  | `mixed`   | An example value found in article data endpoint. e.g. `1`                                                                           |
| `data<:property_name>.code_list`      | `?string` | If codelist associated the URL to code list e.g. `https://s01.cyclesoftware.nl/api/v4/articledata/codelist/article_main_group.json` |

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
        "fr": "Fonctionnement de la poign\u00e9e"
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
        "fr": "Ann\u00e9e mod\u00e8le"
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
        "fr": "URL de l'image haute r\u00e9solution"
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
        "fr": "Texte du re\u00e7u"
      },
      "example_value": {
        "user": "Kassabontekst stored in account",
        "nl": "Omschrijving - Kassabontekst",
        "en": "Description - Receipt text",
        "fr": "Description - Texte du re\u00e7u"
      }
    }
  }
}
```

## Code lists - V4 ##

Get code list entries.

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
      "description_international": "1",
      "description_nl": "Fietsen",
      "description_fr": "V\u00e9los",
      "description_en": "Bikes",
      "description_de": "Radfahren"
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "2",
      "description_international": "2",
      "description_nl": "O&A",
      "description_fr": "Pi\u00e8ces et accessoires",
      "description_en": "Parts and accessories",
      "description_de": "Teile und Zubeh\u00f6r"
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "3",
      "description_international": "3",
      "description_nl": "Kleding",
      "description_fr": "V\u00eatements",
      "description_en": "Clothing",
      "description_de": "Kleidung"
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "4",
      "description_international": "4",
      "description_nl": "Fitness",
      "description_fr": "Fitness",
      "description_en": "Fitness",
      "description_de": "Fitness"
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "5",
      "description_international": "5",
      "description_nl": "Occasions/Doorlevering",
      "description_fr": "Occasions / Livraison",
      "description_en": "Second hand / b2b sales",
      "description_de": "Anl\u00e4sse / Lieferung"
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "6",
      "description_international": "6",
      "description_nl": "Overigen",
      "description_fr": "Autres",
      "description_en": "Miscellaneous",
      "description_de": "Andere"
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "7",
      "description_international": "7",
      "description_nl": "Bromfietsen",
      "description_fr": "Cyclomoteurs",
      "description_en": "Mopeds",
      "description_de": "Mopeds"
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "8",
      "description_international": "8",
      "description_nl": "Bromfietsonderdelen",
      "description_fr": "Pi\u00e8ces de cyclomoteur",
      "description_en": "Moped parts",
      "description_de": "Moped Teile"
    },
    {
      "codelist": "codelist:article_main_group",
      "code": "9",
      "description_international": "9",
      "description_nl": "Tarieven",
      "description_fr": "Tarifs",
      "description_en": "Rates",
      "description_de": "Preise"
    }
  ]
}
```
