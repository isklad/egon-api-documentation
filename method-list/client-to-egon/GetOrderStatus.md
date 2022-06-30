# GetOrderStatus

The method returns the current status information for the order

## Input parameters:
| parameter           |     |  format   | allowed values |     mandatory      | description              |
|:--------------------|:----|:---------:|:--------------:|:------------------:|:-------------------------|
| `order_id`          |     | (Integer) |      [^1]      | :heavy_check_mark: | Part number in the order |
| `original_order_id` |     | (Integer) |      [^1]      | :heavy_check_mark: | obj. at the client       |

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
    "req_method": "GetOrderStatus",
    "req_data": {
      "order_id": 1,
      "original_order_id": 1223456
    }
  }
}


```


## Output parameters:

| parameter                 |                 |                                    |  format   | description                                    |
|---------------------------|-----------------|------------------------------------|:---------:|------------------------------------------------|
| `order_original_id`       |                 |                                    | (Integer) | Order number at client                         |
| `reference_number`        |                 |                                    | (String)  | Reference nr of Order                          |
| `order_id`                |                 |                                    | (Integer) | Order number in iSklad                         |
| `status_id`               |                 |                                    | (Integer) | Order status ID                                |
| `status_name`             |                 |                                    | (String)  | Order status description                       |
| `change_timestamp`        |                 |                                    | (String)  | Date and time of change                        |
| `delivery_id`             |                 |                                    | (Integer) |                                                |
| `Packages`                |                 |                                    |  (Array)  |                                                |
|                           | `package_nr`    |                                    | (String)  | Tracking number                                |
|                           | `tracking_url`  |                                    | (String)  | Tracking URL                                   |
|                           | `tracking_data` |                                    |  (Array)  | Tracking Data                                  |
|                           |                 | `timestamp`                        | (String)  | Time from State                                |
|                           |                 | `shipment_status`                  | (Integer) | Status code from the codebook                  |
|                           |                 | `shipment_note`                    | (String)  | The name of the status from the dial           |
|                           |                 | `shipment_status_delivery_company` | (Integer) | Status ID from courier company                 |
|                           |                 | `shipment_note_delivery_company`   | (String)  | The name of the state from the courier company |
| `shipp_company_id`        |                 |                                    | (Integer) | Carrier ID                                     |
| `shipp_company`           |                 |                                    | (String)  | Name of the carrier                            |
| `estimated_delivery_time` |                 |                                    | (String)  | Estimated delivery time                        |
| `total_cost`              |                 |                                    | (Decimal) | Total expense                                  |
| `cost_by_item`            |                 |                                    |  (Array)  | Costs per individual items                     |
|                           | `item_id`       |                                    | (Integer) |                                                |
|                           | `name`          |                                    | (String)  |                                                |
|                           | `price`         |                                    | (Decimal) |                                                |

## Sample response

```json
{
  
  
  
  
}
```


[^1]: - only one of them is required