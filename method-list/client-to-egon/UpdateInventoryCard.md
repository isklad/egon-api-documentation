# UpdateInventoryCard

This method modifies (if it already exists) or inserts (if not yet) a product card into the system.

## Input parameters

| parameter                 |              | format    | mandatory          | description                                                                |
|---------------------------|--------------|-----------|--------------------|----------------------------------------------------------------------------|
| `item_id`                 |              | (integer) | :heavy_check_mark: | inventory id from your shop/software                                       |
| `shop_setting_id`         |              | (integer) |                    | id of your shop setting (if not filled, your first active shop is selected) |
| `catalog_id`              |              | (string)  |                    | catalog number                                                             |
| `parent_catalog_id`       |              | (string)  |                    | parent's catalog number                                                    |
| `name`                    |              | (string)  | :heavy_check_mark: | product  name                                                              |
| `mj`                      |              | (string)  |                    | unit of measure                                                            |
| `ean`                     |              | (string)  |                    | EAN barcode                                                                |
| `enabled`                 |              | (integer) |                    | allowed on the web                                                         |
| `category`                |              | (string)  |                    | Fields of categories, tree structure                                       |
| `producer`                |              | (string)  |                    | manufacturer                                                               |
| `price_without_tax`       |              | (decimal) |                    | Price without VAT                                                          |
| `old_price_without_tax`   |              | (decimal) |                    | old price excluding VAT                                                    |
| `tax`                     |              | (decimal) |                    | value of VAT                                                               |
| `supplier`                |              | (string)  |                    | the name of the main contractor                                            |
| `supplier_other`          |              | (array)   |                    | Field of other suppliers                                                   |
| `short_description`       |              | (string)  |                    | short description                                                          |
| `long_description`        |              | (string)  |                    | long description                                                           |
| `min_order_count`         |              | (integer) |                    | min. amount                                                                |
| `tech_char`               |              | (array)   |                    | technical characteristics                                                  |
| `tech_param`              |              | (array)   |                    | technical parameters of the variants                                       |
| `images`                  |              | (array)   |                    | Images field                                                               |
|                           | `url`        | (string)  |                    | link to a photo                                                            |
|                           | `order`      | (integer) |                    | display order - the highest number is the main photo                       |
|                           | `enabled`    | (integer) |                    | whether this photo is enabled (view)                                       |
| `is_electronic_product`   |              | (integer) |                    | lectronic (intangible) product, values 0/1                                 |
| `declaration_description` |              | (string)  |                    | Product description for customs declaration                                |
| `commodity_code`          |              | (string)  |                    | HS code (for customs declaration)                                          |
| `accessories`             |              | (array)   |                    | If it is combined card, the field of subcards is sent here                 |
|                           | `item_id`    | (integer) |                    | ITEM_ID of stock card, which belongs under the combined card               |
|                           | `count`      | (integer) |                    | Count of a stock card, that belongs under the combined card                |

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

## Output parameters

| parameter      | format      | description                                 |
|----------------|-------------|---------------------------------------------|
| `inventory_id` | (integer)   | created or updated inventory card id        |

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