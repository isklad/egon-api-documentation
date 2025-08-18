# CreateMyOrderOTP

Creates an OTP (one-time-password) for the MyOrder orders page, which allows you to view the order details without
logging in to the system.

## :arrow_forward: Input parameters:

| parameter           |                  |  format   |                        allowed values                         | mandatory / default value | description             |
|:--------------------|:-----------------|:---------:|:-------------------------------------------------------------:|:-------------------------:|:------------------------|
| `order_id`          |                  | (integer) |                               -                               |  :heavy_check_mark: [^1]  | Producer name           |
| `original_order_id` |                  | (string)  |                               -                               |  :heavy_check_mark: [^1]  | Order id from your shop |
| `shop_setting_id`   |                  | (integer) | [link](https://egon.isklad.com/klient/settings-shop-settings) |  :heavy_check_mark: [^2]  | Set-to-order setting ID |

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
    "req_method": "CreateMyOrderOTP",
    "req_data": {
      "order_id": 123456789
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
    "req_method": "CreateMyOrderOTP",
    "req_data": {
      "original_order_id": "123456",
      "shop_setting_id": 1
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter               |  format  | description                                                        |
|:------------------------|:--------:|:-------------------------------------------------------------------|
| `myorder_url`           | (string) | URL to the MyOrder page, order detail                              |
| `myorder_url_otp`       | (string) | [^3] URL to the MyOrder page, order detail, only one-time-password |
| `myorder_url_otp_claim` | (string) | [^3] URL to the MyOrder page, claim detail, only one-time-password |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 401,
  "resp_note": "401: Entry Created",
  "response": {
    "myorder_url": "https://domain.tld/...",
    "myorder_url_otp": "https://domain.tld/...",
    "myorder_url_otp_claim": "https://domain.tld/..."
    "resp_code": 401,
    "resp_note": "401: Entry Created"
  }
}
```

[^1]: - mandatory only one of them, `order_id` has a priority if both filled  
[^2]: - mandatory only if you dont specify `order_id`
[^3]: - OTP (one time password) is the same for all links, so if you use `myorder_url_otp` you cant use
`myorder_url_otp_claim` and vice versa
