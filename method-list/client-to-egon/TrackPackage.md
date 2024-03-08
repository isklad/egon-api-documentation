# TrackPackage ![deprecated](../../assets/images/deprecated.png)

The method detects the status of the embedded mail through [CreatePackage](CreatePackage.md). Returns tracking
information.

## :arrow_forward: Input parameters:

| parameter           |     |     format     | allowed values | mandatory / default value | description                                                                        |
|:--------------------|:----|:--------------:|:--------------:|:-------------------------:|:-----------------------------------------------------------------------------------|
| `order_id `         |     | (integer/null) |       -        |  :heavy_check_mark: [^1]  | Order id from egon (previously received from [CreateNewOrder](CreateNewOrder.md))  |
| `original_order_id` |     | (string/null)  |       -        |  :heavy_check_mark: [^1]  | Order id from your shop (previously passed to [CreateNewOrder](CreateNewOrder.md)) |
| `package_id`        |     |   (Integer)    |       -        |  :heavy_check_mark: [^1]  | Package number from the system                                                     |
| `delivery_number`   |     |    (String)    |       -        |  :heavy_check_mark: [^1]  | EAN shipments from the system                                                      |

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
    "req_method": "TrackPackage",
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
    "req_method": "TrackPackage",
    "req_data": {
      "order_id": 123456789,
      "original_order_id": "123456",
      "package_id": 1549897,
      "delivery_number": "ABC123456"
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter                 |                                    |   format   | description                                    |
|:--------------------------|:-----------------------------------|:----------:|:-----------------------------------------------|
| `order_id`                |                                    | (Integer)  | Order id from egon                             |
| `status_id`               |                                    | (Integer)  | Order Status ID by dial                        |
| `package_id`              |                                    | (Integer)  | Package ID                                     |
| `delivery_number`         |                                    |  (String)  | Tracking number                                |
| `delivery_label`          |                                    |  (String)  | Address Tag                                    |
| `total_cost`              |                                    | (Decimal)  | Total cost                                     |
| `tracking_data`           |                                    |  (Array)   | Field with data from tracking                  |
|                           | `timestamp`                        | (Datetime) | Time from state                                |
|                           | `shipment_status`                  | (Integer)  | Status code from the codebook                  |
|                           | `shipment_note`                    |  (String)  | The name of the status from the dial           |
|                           | `shipment_status_delivery_company` | (Integer)  | Status ID from courier company                 |
|                           | `shipment_note_delivery_company`   |  (String)  | The name of the state from the courier company |
| `tracking_url`            |                                    |  (String)  | Track tracking URL                             |
| `estimated_delivery_time` |                                    |  (String)  | Estimated delivery time                        |
| `order_errors`            |                                    |  (Array)   | Wrong order parameters                         |

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
    "resp_data": [
      {
        "order_id": 123456789,
        "order_status_id": 123,
        "package_id": 123456789,
        "delivery_number": "589758426",
        "delivery_label": "https://domain.tld/example.pdf",
        "total_cost": 3.89,
        "tracking_data": [
          {
            "timestamp": "2022-05-27 05:45:07",
            "shipment_status": 1,
            "shipment_note": "Carrier accepted the data for the shipment",
            "shipment_status_delivery_company": "900",
            "shipment_note_delivery_company": "We are waiting for the shipment to be accepted for transport.[ ]"
          },
          {
            "timestamp": "2021-05-27 05:45:07",
            "shipment_status": 1,
            "shipment_note": "Carrier accepted the data for the shipment",
            "shipment_status_delivery_company": "900",
            "shipment_note_delivery_company": "We are waiting for the shipment to be accepted for transport. [ ]"
          }
        ],
        "tracking_url": "https://domain.tld/example/main2.aspx?cls=Package&idSearch=589758426",
        "estimated_delivery_time": "2022-05-28",
        "order_errors": []
      }
    ]
  }
}
```

[^1]: - You do not need to specify all of these parameters, just one (for example, order_id) - the presence of the data
is detected in order as in the request. 

