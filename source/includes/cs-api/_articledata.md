# Article data #

The articledata APIs are designed for pulling article-information for e-commerce environments.

***Authentication***

- Basic HTTP Authentication
- Scope(s): `e-commerce`

## Articledata ##

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

In every response you'll find a path to the next resultset. In the example the next resultset is `/app/api/v3/articledata/750-750-0/`. If `next_resultset` is null no additional data is available.

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


## Articledata definitions ##

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
