# UpdateInventoryCard

This method modifies (if it already exists) or inserts (if not yet) a product card into the system.

## :arrow_forward: Input parameters:

| parameter                 |           |  format   |                        allowed values                        | mandatory / default value | description                                                  |
|:--------------------------|:----------|:---------:|:------------------------------------------------------------:|:-------------------------:|:-------------------------------------------------------------|
| `item_id`                 |           | (Integer) |                              -                               |    :heavy_check_mark:     | Inventory ID from your shop/software                         |
| `shop_setting_id`         |           | (Integer) | [link](https://egon.isklad.eu/klient/settings-shop-settings) |    :heavy_check_mark:     | Set-to-order setting ID                                      |
| `catalog_id`              |           | (String)  |                              -                               |                           | Catalog number                                               |
| `parent_catalog_id`       |           | (String)  |                              -                               |                           | Parent's catalog number                                      |
| `name`                    |           | (String)  |                              -                               |    :heavy_check_mark:     | Product  name                                                |
| `mj`                      |           | (String)  |                              -                               |                           | Unit of measure                                              |
| `ean`                     |           | (String)  |                              -                               |                           | EAN barcode                                                  |
| `enabled`                 |           | (Integer) |                              -                               |                           | Allowed on the web                                           |
| `category`                |           |  (Array)  |                              -                               |                           | Fields of categories, tree structure                         |
| `producer`                |           | (String)  |                              -                               |                           | Manufacturer                                                 |
| `price_without_tax`       |           | (Decimal) |                              -                               |                           | Price without VAT                                            |
| `old_price_without_tax`   |           | (Decimal) |                              -                               |                           | Old price excluding VAT                                      |
| `tax`                     |           | (Decimal) |                              -                               |                           | Value of VAT                                                 |
| `supplier`                |           | (String)  |                              -                               |                           | The name of the main contractor                              |
| `supplier_other`          |           |  (Array)  |                              -                               |                           | Field of other suppliers                                     |
| `short_description`       |           | (String)  |                              -                               |                           | Short description                                            |
| `long_description`        |           | (String)  |                              -                               |                           | Long description                                             |
| `min_order_count`         |           | (Integer) |                              -                               |                           | Min. amount                                                  |
| `tech_char`               |           |  (Array)  |                              -                               |                           | Technical characteristics                                    |
| `tech_param`              |           |  (Array)  |                              -                               |                           | Technical parameters of the variants                         |
| `images`                  |           |  (Array)  |                              -                               |                           | Images field                                                 |
|                           | `url`     | (String)  |                              -                               |                           | Link to a photo                                              |
|                           | `order`   | (Integer) |                              -                               |                           | Display order - the highest number is the main photo         |
|                           | `enabled` | (Integer) |                              -                               |                           | Whether this photo is enabled (view)                         |
| `is_electronic_product`   |           | (Integer) |                              -                               |                           | Electronic (intangible) product, values 0/1                  |
| `declaration_description` |           | (String)  |                              -                               |                           | Product description for customs declaration                  |
| `commodity_code`          |           | (String)  |                              -                               |                           | HS code (for customs declaration)                            |
| `accessories`             |           |  (Array)  |                              -                               |                           | If it is combined card, the field of subcards is sent here   |
|                           | `item_id` | (Integer) |                              -                               |                           | ITEM_ID of stock card, which belongs under the combined card |
|                           | `count`   | (Integer) |                              -                               |                           | Count of a stock card, that belongs under the combined card  |
| `weight_grams`            |           | (Integer) |                              -                               |        default: 0         | Weigh of a product in grams                                  |

### Sample requests

#### Minimal

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    "req_method": "UpdateInventoryCard",
    "req_data": {
      "item_id": 123456,
      "shop_setting_id": 1,
      "name": "product name"
    }
  }
}

```

#### Advanced

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    "req_method": "UpdateInventoryCard",
    "req_data": {
      "item_id": 123456,
      "shop_setting_id": 1,
      "catalog_id": "A1A",
      "parent_catalog_id": "A1",
      "name": "product name",
      "mj": "pcs",
      "ean": "123456789012",
      "enabled": 1,
      "category": [
        "category name"
      ],
      "producer": "my producer",
      "price_without_tax": 1.25,
      "old_price_without_tax": 1.55,
      "tax": 20,
      "supplier": "my main supplier",
      "supplier_other": [
        "other supplier"
      ],
      "short_description": "product description",
      "long_description": "long product description",
      "min_order_count": 1,
      "tech_char": {
        "param_1": "param value"
      },
      "tech_param": {
        "param_1": "param value"
      },
      "images": [
        {
          "url": "https://domain.tld/img1.jpg",
          "order": 1,
          "enabled": 1
        }
      ],
      "is_electronic_product": 0,
      "commodity_code": null,
      "declaration_description": null,
      "accessories": [
        {
          "item_id": "123456",
          "count": 1
        },
        {
          "item_id": "1234567",
          "count": 2
        }
      ]
    }
  }
}
```

## :arrow_forward: Output parameters

| parameter      |  format   | description                          |
|:---------------|:---------:|:-------------------------------------|
| `inventory_id` | (integer) | created or updated inventory card id |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 402,
  "resp_note": "402: Entry Updated",
  "response": {
    "resp_code": 402,
    "resp_message": "402: Entry Updated",
    "resp_data": {
      "inventory_id": 123
    }
  }
}
```