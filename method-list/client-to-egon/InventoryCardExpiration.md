# InventoryCardExpiration

Method returns products and their expirations

## :arrow_forward: Input parameters:

| parameter            |     |  format   | allowed values | mandatory / default value | description                       |
|:---------------------|:----|:---------:|:--------------:|:-------------------------:|:----------------------------------|
| `item_id_list`       |     |  (Array)  |       -        |    :heavy_check_mark:     | Field item_id of stock cards [^1] |
| `include_non_paired` |     | (Integer) |     0 / 1      |    :heavy_check_mark:     | Return unpaired cards, too        |


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
    "req_method": "InventoryCardExpiration",
    "req_data": {
      "item_id_list": [111111],
      "include_non_paired": 1
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter          |              |                        |                        |                   |  format   | description                                                      |
|:-------------------|:-------------|:-----------------------|:-----------------------|:------------------|:---------:|:-----------------------------------------------------------------|
| `inventory_list`   |              |                        |                        |                   | (Object)  |                                                                  |
|                    | `paired`     |                        |                        |                   | (Object)  |                                                                  |
|                    |              | `inventoryItemId`      |                        |                   | (Object)  |                                                                  |
|                    |              |                        | `warehouseInventoryId` |                   | (Object)  |                                                                  |
|                    |              |                        |                        | `expiration_date` | (String)  | Expiration date                                                  |
|                    |              |                        |                        | `count `          | (Integer) | quantity / count ???                                             |
|                    | `non_paired` |                        |                        |                   | (Object)  |                                                                  |
|                    |              | `warehouseInventoryId` |                        |                   | (Object)  |                                                                  |
|                    |              |                        | `expiration_date`      |                   | (String)  | Expiration date                                                  |
|                    |              |                        | `count `               |                   | (Integer) | quantity / count ???                                             |
| `inventory_detail` |              |                        |                        |                   | (Object)  |                                                                  |
|                    | `????`       |                        |                        |                   | (Object)  |                                                                  |
|                    |              | `id`                   |                        |                   | (Integer) | ID                                                               |
|                    |              | `item_id`              |                        |                   | (Integer) | Item ID form your shop                                           |
|                    |              | `name`                 |                        |                   | (String)  | Product Name                                                     |
|                    |              | `count_types`          |                        |                   | (Object)  |                                                                  |
|                    |              |                        | `all`                  |                   | (Integer) | Counts of all item physically on stock (for accounting purposes) |
|                    |              |                        | `expired`              |                   | (Integer) | Count of expired                                                 |
|                    |              |                        | `damaged`              |                   | (Integer) | Count of damaged                                                 |
|                    |              |                        | `ordered`              |                   | (Integer) | Count of ordered                                                 |
|                    |              |                        | `reserved`             |                   | (Integer) | Count of reserved                                                |


### Sample response
```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 200,
  "resp_note": "200: OK",
  "response": {
    "success": true,
    "inventory_list": {
      "paired": {
        "59333": {
          "1120": [
            {
              "expiration_date": null,
              "count": 0
            }
          ]
        }
      }
    },
    "inventory_details": {
      "2": {
        "id": 2,
        "item_id": 11111,
        "name": "PRODUCT NAME",
        "count_types": {
          "all": 0,
          "expired": 0,
          "damaged": 0,
          "ordered": 0,
          "reserved": 0
        }
      }
    },
    "resp_code": 200,
    "resp_note": "200: OK"
  }
}
```


[^1]: - If the field is empty then all ..... ??????