# GetOrderInventoryExpiration

The method gains information about items sent out (items added to shipment) and their expiration

## Input parameters:
| parameter           |     |  format   | allowed values |     mandatory      | description                    |
|:--------------------|:----|:---------:|:--------------:|:------------------:|:-------------------------------|
| `original_order_id` |     | (Integer) |                | :heavy_check_mark: | Original order ID              |
| `order_id`          |     | (Integer) |                | :heavy_check_mark: | iSklad order number (optional) |

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
    "req_method": "GetOrderInventoryExpiration",
    "req_data": {
      "original_order_id": 1223456,
      "order_id": 1
    }
  }
}


```


## Output parameters:

| parameter  |                  |  format   | description             |
|------------|------------------|:---------:|-------------------------|
| `order_id` |                  | (Integer) | iSklad order number     |
| `data`     |                  |  (Array)  | Field of sent out items |
|            | `item_id`        | (Integer) | ITEM_ID of item         |
|            | `catalog_number` | (String)  | Catalog number of item  |
|            | `expiration`     | (String)  | Expiration              |
|            | `count`          | (Integer) | Count                   |
|            | `price`          | (Decimal) | Price without VAT       |
|            | `price_with_tax` | (Decimal) | Price with VAT          |
|            | `tax`            | (Decimal) | VAT rate in%            |


## Sample response

```json
{
  
  
  
  
}
```
