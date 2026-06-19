# SettlementItemDetail

List the individual accounted entries (per order / package) of a single monthly settlement item. 

## :arrow_forward: Input parameters:

| parameter       |          |      |  format   | allowed values |     mandatory      | description                 |
|:----------------|:---------|------|:---------:|:--------------:|:------------------:|:----------------------------|
| `settlement_id` |          |      | (Integer) |       -        | :heavy_check_mark: | settlement ID               |
| `item_id`       |          |      | (Integer) |       -        | :heavy_check_mark: | ITEM_ID of the monthly item |

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
    "req_method": "SettlementItemDetail",
    "req_data": {
      "settlement_id": 38303,
      "item_id": 2
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter       |               |      |     format     | description                                   |
|:----------------|:--------------|------|:--------------:|:----------------------------------------------|
| `settlement_id` |               |      |   (Integer)    | Settlement ID                                 |
| `item_id`       |               |      |   (Integer)    | ITEM_ID of the monthly item                   |
| `item_name`     |               |      |    (String)    | Item name                                     |
| `entries`       |               |      |    (Array)     | Individual accounted entries                  |
|                 | `created_at`  |      |   (DateTime)   | format Y-m-d H:i:s                            |
|                 | `referer`     |      |    (String)    | Entry reference note                          |
|                 | `order_id`    |      | (Integer/null) | Related order ID                              |
|                 | `package_id`  |      | (Integer/null) | Related package ID                            |
|                 | `count`       |      |    (Float)     | Entry count                                   |
|                 | `unit_price`  |      |    (Float)     | Unit price, without VAT                       |
|                 | `total_price` |      |    (Float)     | Entry total (count * unit price), without VAT |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 403,
  "resp_note": "403: Content Found",
  "response": {
    "resp_code": 403,
    "resp_message": "403: Content Found",
    "resp_data": {
      "settlement_id": 38303,
      "item_id": 2,
      "item_name": "ITEM_NAME",
      "entries": [
        {
          "created_at": "2024-06-01 12:00:00",
          "referer": "REFERER",
          "order_id": 123456,
          "package_id": 654321,
          "count": 1,
          "unit_price": 0.15,
          "total_price": 0.15
        }
      ]
    }
  }
}
```
