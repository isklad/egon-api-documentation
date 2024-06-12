# StockMovements

List the stock movements for the specified date range.

## :arrow_forward: Input parameters:

| parameter       |          |      |   format   | allowed values |     mandatory      | description        |
|:----------------|:---------|------|:----------:|:--------------:|:------------------:|:-------------------|
| `datetime_from` |          |      | (DateTime) |       -        | :heavy_check_mark: | format Y-m-d H:i:s |
| `datetime_to`   |          |      | (DateTime) |       -        | :heavy_check_mark: | format Y-m-d H:i:s |

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
    "req_method": "StockMovements",
    "req_data": {
      "datetime_from": "2024-06-01 00:00:00",
      "datetime_to": "2024-06-01 23:59:59"
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter            |                  |        |   format   | description                                    |
|:---------------------|:-----------------|--------|:----------:|:-----------------------------------------------|
| `created_at`         |                  |        | (DateTime) | format Y-m-d H:i:s                             |
| `inventory`          |                  |        |  (Object)  | Inventory details                              |
|                      | `inventory_id`   |        | (Integer)  | ID of the movement inventory                   | 
|                      | `item_id`        |        |  (String)  | ITEM_ID of the paired inventory                | 
|                      | `catalog_nr`     |        |  (String)  | Catalog number of the paired inventory         | 
|                      | `inventory_name` |        |  (String)  | Name of the paired inventory                   |
| `document`           |                  |        |  (Object)  | Movement document details                      |
|                      | `id`             |        | (Integer)  | Document ID                                    |
|                      | `type_name`      |        |  (String)  | Document type name                             |
|                      | `source`         |        | (Integer)  | Document source ID (package, order, ...)       |
|                      | `direction`      |        |  (String)  | in/out                                         |
| `count`              |                  |        | (Integer)  | inventory movement count                       |
| `smallest_count`     |                  |        | (Integer)  | smallest inventory movement count              |
| `in_package_box_id`  |                  |        | (Integer)  | package box id - in case of incoming products  |
| `in_package_box_ean` |                  |        |  (String)  | package box ean - in case of incoming products |

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
      "stock_movements": [
        {
          "created_at": "2024-06-01 12:00:00",
          "inventory": {
            "inventory_id": 123,
            "item_id": "ITEM_ID",
            "catalog_nr": "CATALOG_NR",
            "inventory_name": "INVENTORY_NAME"
          },
          "document": {
            "id": 123,
            "type_name": "TYPE_NAME",
            "source": 123,
            "direction": "in"
          },
          "count": 1,
          "smallest_count": 10,
          "in_package_box_id": 123,
          "in_package_box_ean": "IN_PACKAGE_BOX_EAN"
        }
      ]
    }
  }
}
```
