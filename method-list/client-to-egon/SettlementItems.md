# SettlementItems

List the items (accounted breakdown) of a single settlement. Returns the grouped monthly items and the manual items.

## :arrow_forward: Input parameters:

| parameter       |          |      |  format   | allowed values |     mandatory      | description   |
|:----------------|:---------|------|:---------:|:--------------:|:------------------:|:--------------|
| `settlement_id` |          |      | (Integer) |       -        | :heavy_check_mark: | settlement ID |

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
    "req_method": "SettlementItems",
    "req_data": {
      "settlement_id": 38303
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter       |               |      |  format   | description                                                           |
|:----------------|:--------------|------|:---------:|:----------------------------------------------------------------------|
| `settlement_id` |               |      | (Integer) | Settlement ID                                                         |
| `items`         |               |      |  (Array)  | List of settlement items                                              |
|                 | `type`        |      | (String)  | Item type: `monthly` or `manual`                                      |
|                 | `id`          |      | (Integer) | Monthly item: ITEM_ID, manual item: record ID                         |
|                 | `name`        |      | (String)  | Item name                                                             |
|                 | `count`       |      |  (Float)  | Item count                                                            |
|                 | `mj`          |      | (String)  | Measure unit                                                          |
|                 | `total_price` |      |  (Float)  | Total item amount, without VAT                                        |
|                 | `has_detail`  |      | (Boolean) | Whether the item has a breakdown available via `SettlementItemDetail` |

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
      "items": [
        {
          "type": "monthly",
          "id": 2,
          "name": "ITEM_NAME",
          "count": 120,
          "mj": "ks",
          "total_price": 240.5,
          "has_detail": true
        },
        {
          "type": "manual",
          "id": 555,
          "name": "MANUAL_ITEM_NAME",
          "count": 1,
          "mj": "x",
          "total_price": 50,
          "has_detail": false
        }
      ]
    }
  }
}
```
