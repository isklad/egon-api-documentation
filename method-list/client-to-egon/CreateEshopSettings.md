# CreateEshopSettings

Creates settings for another eshop

# _Ktore paraemetre su povinne_

## Input parameters:
| parameter                         |      |  format   | allowed values |     mandatory      | description                      |
|:----------------------------------|:-----|:---------:|:--------------:|:------------------:|:---------------------------------|
| `name`                            |      | (String)  |                | :heavy_check_mark: | Eshop name                       |
| `url`                             |      | (String)  |                |                    | Eshop address                    |
| `email`                           |      | (String)  |                |                    | Eshop Email                      |
| `phone`                           |      | (String)  |                |                    | Eshop Phone                      |
| `listener_url`                    |      | (String)  |                |                    | URL for reverse API (listener)   |
| `enable_import_cards `            |      | (Integer) |     0 / 1      |                    | Allow import of stock cards      |
| `enable_import_orders `           |      | (Integer) |     0 / 1      |                    | Allow import of the orders       |
| `enable_api_listener`             |      | (Integer) |     0 / 1      |                    | Allow api listener               |
| `enable_inventory_status_update ` |      | (Integer) |     0 / 1      |                    | Allow updates of stock inventory |
| `enable_tracking_update `         |      | (Integer) |     0 / 1      |                    | Allow tracking status updates    |


## Sample request

### Minimal

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    "req_method": "CreateEshopSettings",
    "req_data": {
      "name": "name",
      "url": "https://domain.tld/",
      "email": "abcd@defgh.com",
      "phone": "+421 123 567 789",
      "listener_url": "https://domain.tld/",
      "enable_import_cards": 0,
      "enable_import_orders": 0,
      "enable_api_listener": 0,
      "enable_inventory_status_update": 0,
      "enable_tracking_update": 0
    }
  }
}
```

### Advanced
```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    
  }
}
```

# _doplnit parametre a response_
## Output parameters:

| parameter                |     |  format   | description                       |
|--------------------------|-----|:---------:|-----------------------------------|
| `SHOP_SETTING_ID`        |     | (Integer) | Eshop ID                          |
| `SHOP_RECIPIENT_ADDRESS` |     | (String)  | Shop address (for incoming goods) |


## Sample response

```json
{
  
  
  
}
```