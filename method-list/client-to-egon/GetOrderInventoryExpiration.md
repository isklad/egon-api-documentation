# GetOrderInventoryExpiration

The method gains information about items sent out (items added to shipment) and their expiration

## :arrow_forward: Input parameters:

| parameter           |     |     format     | allowed values | mandatory / default value | description                                                                        |
|:--------------------|:----|:--------------:|:--------------:|:-------------------------:|:-----------------------------------------------------------------------------------|
| `order_id `         |     | (integer/null) |       -        |  :heavy_check_mark: [^1]  | Order id from egon (previously received from [CreateNewOrder](CreateNewOrder.md))  |
| `original_order_id` |     | (string/null)  |       -        |  :heavy_check_mark: [^1]  | Order id from your shop (previously passed to [CreateNewOrder](CreateNewOrder.md)) |

### Sample request

#### Minimal
```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    "req_method": "GetOrderInventoryExpiration",
    "req_data": {
      "order_id": 4886010
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
    "req_method": "GetOrderInventoryExpiration",
    "req_data": {
      "original_order_id": 1223456,
      "order_id": 4886010
    }
  }
}


```

## :arrow_forward: Output parameters:

| parameter   |                   |  format   | description              |
|:------------|:------------------|:---------:|:-------------------------|
| `order_id`  |                   | (Integer) | Order id from egon       |
| `data`      |                   |  (Array)  | Field of sent out items  |
|             | `item_id`         | (Integer) | ITEM_ID of item          |
|             | `catalog_number`  | (String)  | Catalog number of item   |
|             | `expiration`      | (String)  | Expiration               |
|             | `price`           | (Decimal) | Price excluding VAT      |
|             | `price_with_tax`  | (Decimal) | Price including VAT      |
|             | `tax`             | (Decimal) | VAT rate in%             |
|             | `count`           | (Integer) | Quantity                 |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 403,
  "resp_note": "403: Content Found",
  "response": {
    "order_id": 4886010,
    "data": [
      {
        "item_id": 19565251231,
        "catalog_number": "561312302",
        "expiration": "2022-07-07",
        "price": 0,
        "price_with_tax": 0,
        "tax": 0,
        "count": 1
      }
    ],
    "resp_code": 403,
    "resp_note": "403: Content Found"
  }
}
```

[^1]: - mandatory only one of them, `order_id` has a priority if both filled