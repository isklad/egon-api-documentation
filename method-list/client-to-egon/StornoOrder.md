# StornoOrder

The method cancels an existing order in the system. Cancellation of orders is only possible in certain situations when
the order is not sent yet. Otherwise, resp_code = 303: Method Not Allowed

## :arrow_forward: Input parameters:

| parameter           |     |     format     |                        allowed values                        | mandatory / default value | description                                                                        |
|:--------------------|:----|:--------------:|:------------------------------------------------------------:|:-------------------------:|:-----------------------------------------------------------------------------------|
| `order_id `         |     | (integer/null) |                              -                               |  :heavy_check_mark: [^1]  | Order id from egon (previously received from [CreateNewOrder](CreateNewOrder.md))  |
| `original_order_id` |     | (string/null)  |                              -                               |  :heavy_check_mark: [^1]  | Order id from your shop (previously passed to [CreateNewOrder](CreateNewOrder.md)) |
| `shop_setting_id`   |     |   (Integer)    | [link](https://egon.isklad.eu/klient/settings-shop-settings) |  :heavy_check_mark: [^2]  | Set-to-order setting ID                                                            |

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
    "req_method": "StornoOrder",
    "req_data": {
      "order_id": 123456789,
      "shop_setting_id": "1"
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
    "req_method": "StornoOrder",
    "req_data": {
      "order_id": 123456789,
      "original_order_id": "123456",
      "shop_setting_id": "1"
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter       |     |  format   | description                         |
|:----------------|:----|:---------:|:------------------------------------|
| `order_id`      |     | (Integer) | Order id from egon                  |
| `new_status_id` |     | (Integer) | The order ID created in the system  |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 402,
  "resp_note": "402: Entry Updated",
  "response": {
    "resp_data": {
      "order_id": 123456789,
      "new_status_id": 9
    },
    "resp_code": 402,
    "resp_note": "402: Entry Updated"
  }
}
```

[^1]: - mandatory only one of them, `order_id` has a priority if both filled  
[^2]: - mandatory if there are multiple e-shops in the account