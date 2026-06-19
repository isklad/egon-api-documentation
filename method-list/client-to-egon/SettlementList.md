# SettlementList

List the issued settlements of the shop for the specified year. All amounts are without VAT (the related
VAT invoice is not part of the settlement).

## :arrow_forward: Input parameters:

| parameter |          |      |  format   | allowed values |     mandatory      | description                |
|:----------|:---------|------|:---------:|:--------------:|:------------------:|:---------------------------|
| `year`    |          |      | (Integer) |       -        | :heavy_check_mark: | settlements year, format Y |

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
    "req_method": "SettlementList",
    "req_data": {
      "year": 2024
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter     |               |      |  format   | description                               |
|:--------------|:--------------|------|:---------:|:------------------------------------------|
| `settlements` |               |      |  (Array)  | List of settlements                       |
|               | `id`          |      | (Integer) | Settlement ID                             |
|               | `year`        |      | (Integer) | Settlement year                           |
|               | `month`       |      | (Integer) | Settlement month                          |
|               | `period`      |      | (String)  | Settlement period, format Y-m             |
|               | `total_price` |      |  (Float)  | Total settlement amount, without VAT      |
|               | `currency`    |      | (String)  | Currency code                             |
|               | `is_paid`     |      | (Boolean) | Whether the related invoice is fully paid |

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
      "settlements": [
        {
          "id": 38303,
          "year": 2024,
          "month": 6,
          "period": "2024-06",
          "total_price": 1234.56,
          "currency": "EUR",
          "is_paid": true
        }
      ]
    }
  }
}
```
