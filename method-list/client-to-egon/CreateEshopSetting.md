# CreateEshopSetting

Creates settings for another eshop.

## :arrow_forward: Input parameters:

| parameter                         |     |  format   | allowed values | mandatory / default value | description                      |
|:----------------------------------|:----|:---------:|:--------------:|:-------------------------:|:---------------------------------|
| `name`                            |     | (String)  |       -        |    :heavy_check_mark:     | Eshop name                       |
| `url`                             |     | (String)  |       -        |    :heavy_check_mark:     | Eshop address                    |
| `email`                           |     | (String)  |       -        |    :heavy_check_mark:     | Eshop Email                      |
| `phone`                           |     | (String)  |       -        |    :heavy_check_mark:     | Eshop Phone                      |
| `listener_url`                    |     | (String)  |       -        |    :heavy_check_mark:     | URL for reverse API (listener)   |
| `enable_import_cards `            |     | (Integer) |     0 / 1      |             0             | Allow import of stock cards      |
| `enable_import_orders `           |     | (Integer) |     0 / 1      |             0             | Allow import of the orders       |
| `enable_api_listener`             |     | (Integer) |     0 / 1      |             0             | Allow api listener               |
| `enable_inventory_status_update ` |     | (Integer) |     0 / 1      |             0             | Allow updates of stock inventory |
| `enable_tracking_update `         |     | (Integer) |     0 / 1      |             0             | Allow tracking status updates    |

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
    "req_method": "CreateEshopSetting",
    "req_data": {
      "name": "name",
      "url": "https://domain.tld/",
      "email": "email@domain.tld",
      "phone": "+421123567789",
      "listener_url": "https://domain.tld/example"
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
    "req_method": "CreateEshopSetting",
    "req_data": {
      "name": "name",
      "url": "https://domain.tld/",
      "email": "email@domain.tld",
      "phone": "+421123567789",
      "listener_url": "https://domain.tld/example",
      "enable_import_cards": 0,
      "enable_import_orders": 0,
      "enable_api_listener": 0,
      "enable_inventory_status_update": 0,
      "enable_tracking_update": 0
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter                 |  format   | description                        |
|:--------------------------|:---------:|:-----------------------------------|
| `SHOP_SETTING_ID`         | (Integer) | Eshop ID                           |
| `SHOP_RECIPIENT_ADDRESS`  | (String)  | Shop address (for incoming goods)  |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 401,
  "resp_note": "401: Entry Created",
  "response": {
    "SHOP_SETTING_ID": 26,
    "SHOP_RECIPIENT_ADDRESS": "26/150001",
    "resp_code": 401,
    "resp_note": "401: Entry Created"
  }
}
```