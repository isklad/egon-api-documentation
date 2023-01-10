# InventoryDetail

Method returns product details (name, count,...)

## :arrow_forward: Input parameters:

| parameter       |     |  format   | allowed values | mandatory / default value | description                                                |
|:----------------|:----|:---------:|:--------------:|:-------------------------:|:-----------------------------------------------------------|
| `item_id_list`  |     |  (Array)  |       -        |    :heavy_check_mark:     | Field item_id of stock cards  (if all, then empty field)   |
| `cached`        |     | (Integer) |     0 / 1      |             0             | cached values - if realtime data are required send value 0 |
| `only_on_stock` |     | (Integer) |     0 / 1      |             0             | only in stock                                              |

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
    "req_method": "InventoryDetail",
    "req_data": {
      "item_id_list": [1]
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
    "req_method": "InventoryDetail",
    "req_data": {
      "item_id_list": [1],
      "cached": 1,
      "only_on_stock": 1
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter           |                |                     |          |   format   | description                                                         |
|:--------------------|:---------------|:--------------------|:---------|:----------:|:--------------------------------------------------------------------|
| `inventory_details` |                |                     |          |  (Array)   |                                                                     |
|                     | `id`           |                     |          | (Integer)  | ID                                                                  |
|                     | `item_id`      |                     |          | (Integer)  | ITEM ID from eshop                                                  |
|                     | `catalog_id`   |                     |          |  (String)  | Catalog nr.                                                         |
|                     | `ean`          |                     |          |  (String)  | EAN                                                                 |
|                     | `name`         |                     |          |  (String)  | Product Name                                                        |
|                     | `count_types`  |                     |          |  (Object)  |                                                                     |
|                     |                | `all`               |          | (Integer)  | Quantity of all items physically on stock (for accounting purposes) |
|                     |                | `expired`           |          | (Integer)  | Quantity of expired items                                           |
|                     |                | `damaged`           |          | (Integer)  | Quantity of damaged items                                           |
|                     |                | `ordered`           |          | (Integer)  | Quantity of ordered items                                           |
|                     |                | `reserved`          |          | (Integer)  | Quantity of reserved items                                          |
|                     |                | `expirationBlocked` |          | (Integer)  | Quantity of blocked items by expiration, but not expired yet        |
|                     |                | `changed_at`        |          | (String)   | Last change datetime                                                |
|                     | `paired_cards` |                     |          |  (Object)  |                                                                     |
|                     |                | `id`                |          | (Integer)  | ID of paired inventory                                              |
|                     |                | `type_id`           |          | (Integer)  | ID of inventory type [^1]                                           |
|                     |                | `size`              |          |  (Object)  |                                                                     |
|                     |                |                     | `width`  | (Integer)  | Width of paired inventory                                           |
|                     |                |                     | `height` | (Integer)  | Height of paired inventory                                          |
|                     |                |                     | `depth`  | (Integer)  | Depth of paired inventory                                           |
|                     |                | `weight`            |          | (Integer)  | Weight of paired inventory                                          |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 200,
  "resp_note": "200: OK",
  "response": {
    "success": true,
    "inventory_details": {
      "240442": {
        "id": 240442,
        "item_id": 1,
        "catalog_id": "test",
        "ean": "unknown ean",
        "name": "test",
        "count_types": {
          "all": 0,
          "expired": 0,
          "damaged": 0,
          "ordered": 1,
          "reserved": 0,
          "expirationBlocked": 0,
          "changed_at": "2022-09-12 11:07:51"
        },
        "paired_cards": []
      }
    },
    "resp_code": 200,
    "resp_note": "200: OK"
  }
}
```

> **![recommended](../../assets/images/recommended.png) formulas:**
> - display on shop: `ALL` - `EXPIRED` - `DAMAGED` - `ORDERED` - `RESERVED`
> - accounting purposes: `ALL`


[^1]: - ID - 0: piece, 1: multiPack, 2: package, 3: pallet