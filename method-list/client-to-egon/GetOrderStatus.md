# GetOrderStatus

The method returns the current status information for the order

## :arrow_forward: Input parameters:

| parameter           |     |     format     | allowed values | mandatory / default value | description                                                                        |
|:--------------------|:----|:--------------:|:--------------:|:-------------------------:|:-----------------------------------------------------------------------------------|
| `order_id `         |     | (integer/null) |       -        |  :heavy_check_mark: [^1]  | Order id from egon (previously received from [CreateNewOrder](CreateNewOrder.md))  |
| `original_order_id` |     | (string/null)  |       -        |  :heavy_check_mark: [^1]  | Order id from your shop (previously passed to [CreateNewOrder](CreateNewOrder.md)) |

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
    "req_method": "GetOrderStatus",
    "req_data": {
      "order_id": 458789
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
    "req_method": "GetOrderStatus",
    "req_data": {
      "order_id": 456879,
      "original_order_id": 1223456
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter                  |                  |                                     |  format   | description                                     |
|:---------------------------|:-----------------|:------------------------------------|:---------:|:------------------------------------------------|
| `order_original_id`        |                  |                                     | (Integer) | Order id from your shop                         |
| `reference_number`         |                  |                                     | (String)  | Reference nr of Order                           |
| `order_id`                 |                  |                                     | (Integer) | Order id from egon                              |
| `status_id`                |                  |                                     | (Integer) | Order status ID                                 |
| `status_name`              |                  |                                     | (String)  | Order status description                        |
| `change_timestamp`         |                  |                                     | (String)  | Date and time of change                         |
| `delivery_id`              |                  |                                     | (Integer) |                                                 |
| `packages`                 |                  |                                     |  (Array)  |                                                 |
|                            | `package_nr`     |                                     | (String)  | Tracking number                                 |
|                            | `tracking_url`   |                                     | (String)  | Tracking URL                                    |
|                            | `tracking_data`  |                                     |  (Array)  | Tracking Data                                   |
|                            |                  | `timestamp`                         | (String)  | Time from State                                 |
|                            |                  | `shipment_status`                   | (Integer) | Status code from the codebook                   |
|                            |                  | `shipment_note`                     | (String)  | The name of the status from the dial            |
|                            |                  | `shipment_status_delivery_company`  | (Integer) | Status ID from courier company                  |
|                            |                  | `shipment_note_delivery_company`    | (String)  | The name of the state from the courier company  |
| `shipp_company_id`         |                  |                                     | (Integer) | Carrier ID                                      |
| `shipp_company`            |                  |                                     | (String)  | Name of the carrier                             |
| `estimated_delivery_time`  |                  |                                     | (String)  | Estimated delivery time                         |
| `total_cost`               |                  |                                     | (Decimal) | Total expense                                   |
| `cost_by_item`             |                  |                                     |  (Array)  | Costs per individual items                      |
|                            | `item_id`        |                                     | (Integer) |                                                 |
|                            | `name`           |                                     | (String)  |                                                 |
|                            | `price`          |                                     | (Decimal) |                                                 |

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
      "order_original_id": "28247",
      "reference_number": "",
      "order_id": 1,
      "status_id": 6,
      "status_name": "is completed",
      "change_timestamp": "2022-07-01 17:38:27",
      "delivery_id": 1,
      "packages": [],
      "shipp_company_id": 1,
      "shipp_company": "isklad Express courier Bratislava",
      "estimated_delivery_time": "2022-07-06",
      "total_cost": 0,
      "cost_by_item": []
    }
  }
}
```

[^1]: - mandatory only one of them, `order_id` has a priority if both filled