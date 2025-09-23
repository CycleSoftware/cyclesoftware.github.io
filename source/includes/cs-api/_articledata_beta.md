# Article data #


## Article batch updates (beta)##

Apply batch updates to articles. Be aware that during the beta-phase the properties may change.

***Authentication mechanism***

- Basic HTTP Authentication
- Scopes: `resources`

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">PATCH</i>
		<h6>/api/beta/articles/batch/update.json</h6>
	</div>
</div>

### Request properties

| Property                                | Type       | Required | Description                                                                                                                                                      |
|-----------------------------------------|------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `updates`                               | `object[]` | `true`   | Array with data objects, maximum of 150 items                                                                                                                    |
| `updates[].barcode`                     | `string`   | `true`   | Barcode of the article e.g. `878825512152`                                                                                                                       |
| `updates[].update_mode`                 | `string`   | `false`  | Update mode e.g. `update_or_create`, `update_only`, `create_only`                                                                                                |
| `updates[].pos_group_id`                | `integer`  | `false`  | POS group ID e.g. `5` see `pos_groups` see `pos_groups` in `/api/v1/common/enum.json`                                                                            |
| `updates[].article_main_group`          | `integer`  | `false`  | Main article group ID e.g. `2` if provided `article_group` and `article_sub_group` are also required. See `/api/v4/articledata/codelist/article_main_group.json` |
| `updates[].article_group`               | `string`   | `false`  | Article group ID e.g. `A`  if provided `article_main_group` and `article_sub_group` are also required. See `/api/v4/articledata/codelist/article_group.json`     |
| `updates[].article_sub_group`           | `integer`  | `false`  | Sub article group ID e.g. `2`  if provided `article_main_group` and `article_group` are also required. See `/api/v4/articledata/codelist/article_sub_group.json` |
| `updates[].brand_name`                  | `string`   | `false`  | Brand name e.g. `SCHWALBE`                                                                                                                                       |
| `updates[].custom_variable_1`           | `string`   | `false`  | Custom variable 1 e.g. `Some Value`                                                                                                                              |
| `updates[].custom_variable_2`           | `string`   | `false`  | Custom variable 2 e.g. `Some Value`                                                                                                                              |
| `updates[].custom_variable_3`           | `string`   | `false`  | Custom variable 3 e.g. `Some Value`                                                                                                                              |
| `updates[].custom_variable_4`           | `string`   | `false`  | Custom variable 4 e.g. `Some Value`                                                                                                                              |
| `updates[].custom_variable_5`           | `string`   | `false`  | Custom variable 5 e.g. `Some Value`                                                                                                                              |
| `updates[].custom_variable_6`           | `string`   | `false`  | Custom variable 6 e.g. `Some Value`                                                                                                                              |
| `updates[].description_en`              | `string`   | `false`  | Description in English e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                                                            |
| `updates[].description_nl`              | `string`   | `false`  | Description in Dutch (generally default description) e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                              |
| `updates[].description_fr`              | `string`   | `false`  | Description in French e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                                                             |
| `updates[].ecommerce`                   | `boolean`  | `false`  | Available for e-commerce e.g. `false`                                                                                                                            |
| `updates[].ecommerce_price_cents`       | `integer`  | `false`  | The e-commerce price in cents e.g. `6290`                                                                                                                        |
| `updates[].ecommerce_promo_price_cents` | `integer`  | `false`  | The e-commerce promo price in cents e.g. `0` (disabled if `0`)                                                                                                   |
| `updates[].ecommerce_promo_price_from`  | `?date`    | `false`  | The date for e-commerce promo price interval start e.g. `2022-01-01` or `null`                                                                                   |
| `updates[].ecommerce_promo_price_until` | `?date`    | `false`  | The date for e-commerce promo price interval until e.g. `2022-01-01` or `null`                                                                                   |
| `updates[].min_stock`                   | `integer`  | `false`  | Minimal stock level e.g. `10`                                                                                                                                    |
| `updates[].max_stock`                   | `integer`  | `false`  | Maximum stock level e.g. `20`                                                                                                                                    |
| `updates[].stock`                       | `integer`  | `false`  | Stock level e.g. `1`. You can not update the stock if stock is already non-zero.                                                                                 |
| `updates[].pos_promo_price_cents`       | `integer`  | `false`  | Promo price in cents e.g. `5750` (disabled if `0`)                                                                                                               |
| `updates[].pos_promo_price_from`        | `?date`    | `false`  | The date for promo price interval start e.g. `2022-01-01` or `null`                                                                                              |
| `updates[].pos_promo_price_until`       | `?date`    | `false`  | The date for promo price interval until e.g. `2022-01-01` or `null`                                                                                              |
| `updates[].pos_sales_price_cents`       | `integer`  | `false`  | The POS sales price in cents e.g. `6290`                                                                                                                         |
| `updates[].purchase_price_cents`        | `integer`  | `false`  | The purchase price in cents e.g. `3624`                                                                                                                          |


### Result properties

| Property                                        | Type       | Nullable | Omittable | Description                                                                                                                                                                                                                                                                                  |
|-------------------------------------------------|------------|----------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `results`                                       | `object[]` | `false`  |           | Array of objects                                                                                                                                                                                                                                                                             |
| `results[].barcode`                             | `string`   | `false`  |           | Barcode of the article e.g. `878825512152`                                                                                                                                                                                                                                                   |
| `results[].result`                              | `string`   | `false`  |           | Result status `success` (all fields updated),  `partial` (not all fields could be updated see `results[].skipped_fields`, `success_with_warnings` (all fields updated with some warnings, see `results[].warnings`), `error` (article not updated or created, see `results[].error.message`) |
| `results[].article`                             | `object`   | `false`  | `Yes`     | Object with resulting article details, omitted when an error occurs                                                                                                                                                                                                                          |
| `results[].article.barcode`                     | `string`   | `false`  |           | Barcode of the article e.g. `878825512152`                                                                                                                                                                                                                                                   |
| `results[].article.store_id`                    | `integer`  | `false`  |           | Store ID related to `stock`, `min_stock`, and `max_stock` e.g. `1`                                                                                                                                                                                                                           |
| `results[].article.update_mode`                 | `string`   | `false`  |           | Update mode e.g. `update_or_create`, `update_only`, `create_only`                                                                                                                                                                                                                            |
| `results[].article.pos_group_id`                | `integer`  | `false`  |           | POS group ID e.g. `5` see `pos_groups` in common enum endpoint                                                                                                                                                                                                                               |
| `results[].article.article_main_group`          | `integer`  | `false`  |           | Main article group ID e.g. `2`                                                                                                                                                                                                                                                               |
| `results[].article.article_group`               | `string`   | `false`  |           | Article group ID e.g. `A`                                                                                                                                                                                                                                                                    |
| `results[].article.article_sub_group`           | `integer`  | `false`  |           | Sub article group ID e.g. `2`                                                                                                                                                                                                                                                                |
| `results[].article.brand_name`                  | `string`   | `false`  |           | Brand name e.g. `SCHWALBE`                                                                                                                                                                                                                                                                   |
| `results[].article.currency`                    | `string`   | `false`  |           | Currency `EUR`                                                                                                                                                                                                                                                                               |
| `results[].article.custom_variable_1`           | `string`   | `false`  |           | Custom variable 1 e.g. `Some Value`                                                                                                                                                                                                                                                          |
| `results[].article.custom_variable_2`           | `string`   | `false`  |           | Custom variable 2 e.g. `Some Value`                                                                                                                                                                                                                                                          |
| `results[].article.custom_variable_3`           | `string`   | `false`  |           | Custom variable 3 e.g. `Some Value`                                                                                                                                                                                                                                                          |
| `results[].article.custom_variable_4`           | `string`   | `false`  |           | Custom variable 4 e.g. `Some Value`                                                                                                                                                                                                                                                          |
| `results[].article.custom_variable_5`           | `string`   | `false`  |           | Custom variable 5 e.g. `Some Value`                                                                                                                                                                                                                                                          |
| `results[].article.custom_variable_6`           | `string`   | `false`  |           | Custom variable 6 e.g. `Some Value`                                                                                                                                                                                                                                                          |
| `results[].article.description_en`              | `string`   | `false`  |           | Description in English e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                                                                                                                                                                                        |
| `results[].article.description_nl`              | `string`   | `false`  |           | Description in Dutch (generally default description) e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                                                                                                                                                          |
| `results[].article.description_fr`              | `string`   | `false`  |           | Description in French e.g. `29x2.25 Racing Ralph SuperRace Addix Speed TLE Skinwall`                                                                                                                                                                                                         |
| `results[].article.ecommerce`                   | `boolean`  | `false`  |           | Available for e-commerce e.g. `false`                                                                                                                                                                                                                                                        |
| `results[].article.ecommerce_price_cents`       | `integer`  | `false`  |           | The e-commerce price in cents e.g. `6290`                                                                                                                                                                                                                                                    |
| `results[].article.ecommerce_promo_price_cents` | `integer`  | `false`  |           | The e-commerce promo price in cents e.g. `0` (disabled if `0`)                                                                                                                                                                                                                               |
| `results[].article.ecommerce_promo_price_from`  | `date`     | `true`   |           | The date for e-commerce promo price interval start e.g. `2022-01-01`                                                                                                                                                                                                                         |
| `results[].article.ecommerce_promo_price_until` | `date`     | `true`   |           | The date for e-commerce promo price interval until e.g. `2022-01-01`                                                                                                                                                                                                                         |
| `results[].article.min_stock`                   | `integer`  | `false`  |           | Minimal stock level e.g. `10`                                                                                                                                                                                                                                                                |
| `results[].article.max_stock`                   | `integer`  | `false`  |           | Maximum stock level e.g. `20`                                                                                                                                                                                                                                                                |
| `results[].article.stock`                       | `integer`  | `false`  |           | Stock level e.g. `1`                                                                                                                                                                                                                                                                         |
| `results[].article.pos_promo_price_cents`       | `integer`  | `false`  |           | Promo price in cents e.g. `5750` (disabled if `0`)                                                                                                                                                                                                                                           |
| `results[].article.pos_promo_price_from`        | `date`     | `true`   |           | The date for promo price interval start e.g. `2022-01-01`                                                                                                                                                                                                                                    |
| `results[].article.pos_promo_price_until`       | `date`     | `true`   |           | The date for promo price interval until e.g. `2022-01-01`                                                                                                                                                                                                                                    |
| `results[].article.pos_sales_price_cents`       | `integer`  | `false`  |           | The POS sales price in cents e.g. `6290`                                                                                                                                                                                                                                                     |
| `results[].article.purchase_price_cents`        | `integer`  | `false`  |           | The purchase price in cents e.g. `3624`                                                                                                                                                                                                                                                      |
| `results[].skipped_fields`                      | `string[]` | `false`  | `Yes`     | Array of fields which are ignored in the update. Omitted if not present                                                                                                                                                                                                                      |
| `results[].warnings`                            | `object[]` | `false`  | `Yes`     | Array of warnings, omitted if status `error` or `success`                                                                                                                                                                                                                                    |
| `results[].warnings[].field`                    | `?string`  | `false`  |           | The field which the warning is related to if applicable e.g. `ecommerce_price_cents`                                                                                                                                                                                                         |
| `results[].warnings[].message`                  | `string`   | `false`  |           | The warning message                                                                                                                                                                                                                                                                          |
| `results[].error`                               | `object`   | `false`  | `Yes`     | Object with error info. Only present when status `error`                                                                                                                                                                                                                                     |
| `results[].error.message`                       | `string`   | `false`  |           | The error message e.g. `Maximaal 150 updates toegestaan per aanvraag`                                                                                                                                                                                                                        |


> HTTP request

```http
PATCH /api/beta/articles/batch/update.json HTTP/1.1
Host: api.cyclesoftware.nl
Authorization: Basic VXNlcm5hbWU6UGFzc3dvcmQ=
Accept-encoding: gzip
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
                    "message": "article_main_group, article_group, article_sub_group zijn verplicht bij update van article_main_group"
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


