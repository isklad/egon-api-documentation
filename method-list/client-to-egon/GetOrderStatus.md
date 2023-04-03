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


| parameter                 |                  |                                    |     format     | description                                                                         |
|:--------------------------|:-----------------|:-----------------------------------|:--------------:|:------------------------------------------------------------------------------------|
| `order_original_id`       |                  |                                    |    (String)    | The original order number for the client                                            |
| `reference_number`        |                  |                                    |    (String)    | Reference Nr. of order                                                              |
| `order_id`                |                  |                                    |   (Integer)    | Order ID from EGON                                                                  |
| `status_id`               |                  |                                    |   (Integer)    | EGON status ID                                                                      |
| `status_name`             |                  |                                    |    (String)    | Status name from EGON                                                               |
| `api_update_enabled`      |                  |                                    |   (Boolean)    | If update over api in this status is enabled then true otherwise false              |
| `change_timestamp`        |                  |                                    |   (Datetime)   | Timestamp of state change                                                           |
| `delivery_id`             |                  |                                    |   (Integer)    | Traffic ID                                                                          |
| `order_items`             |                  |                                    |    (Object)    | Order items                                                                         |
|                           | `ITEM_ID`        |                                    |   (Integer)    | ITEM_ID eshop card                                                                  |
|                           | `COUNT`          |                                    |   (Integer)    | Number of pieces in order                                                           |
|                           | `COUNT_RESERVED` |                                    |   (Integer)    | Number of reserved pieces in the order                                              |
| `packages`                |                  |                                    |    (Array)     |                                                                                     |
|                           | `PACKAGE_NR`     |                                    |    (String)    | Tracking number ![deprecated](../../assets/images/deprecated.png)[^2]               |
|                           | `TRACKING_URL`   |                                    |    (String)    | Tracking link ![deprecated](../../assets/images/deprecated.png)[^1]                 |
|                           | `TRACKING_DATA`  |                                    |    (Array)     | Field with data from tracking ![deprecated](../../assets/images/deprecated.png)[^2] |
|                           |                  | `timestamp`                        |   (Datetime)   | Time from state                                                                     |
|                           |                  | `shipment_status`                  |   (Integer)    | Status code from the codebook                                                       |
|                           |                  | `shipment_note`                    |    (String)    | The name of the status from the dial                                                |
|                           |                  | `shipment_status_delivery_company` |    (String)    | Status ID from courier company                                                      |
|                           |                  | `shipment_note_delivery_company`   |    (String)    | The name of the state from the courier company                                      |
|                           | `IMAGES`         |                                    |    (Array)     | Pictures ![deprecated](../../assets/images/deprecated.png)[^2]                      |
|                           | `WEIGHT`         |                                    |   (Integer)    | Weight ![deprecated](../../assets/images/deprecated.png)[^2]                        |
|                           | `WIDTH`          |                                    |   (Integer)    | Width ![deprecated](../../assets/images/deprecated.png)[^2]                         |
|                           | `HEIGHT`         |                                    |   (Integer)    | Height ![deprecated](../../assets/images/deprecated.png)[^2]                        |
|                           | `DEPTH`          |                                    |   (Integer)    | Depth ![deprecated](../../assets/images/deprecated.png)[^2]                         |
|                           | `LABEL`          |                                    |    (String)    | Label ![deprecated](../../assets/images/deprecated.png)[^2]                         |
|                           | `package_nr`     |                                    |    (String)    | Tracking number                                                                     |
|                           | `tracking_url`  |                                    |    (String)    | Tracking link                                                                       |
|                           | `tracking_data`  |                                    |    (Array)     | Field with data from tracking                                                       |
|                           |                  | `timestamp`                        |   (Datetime)   | Time from state                                                                     |
|                           |                  | `shipment_status`                  |   (Integer)    | Status code from the codebook                                                       |
|                           |                  | `shipment_note`                    |    (String)    | The name of the status from the dial                                                |
|                           |                  | `shipment_status_delivery_company` |    (String)    | Status ID from courier company                                                      |
|                           |                  | `shipment_note_delivery_company`   |    (String)    | The name of the state from the courier company                                      |
|                           | `images`         |                                    |    (Array)     | Pictures                                                                            |
|                           | `weight`         |                                    |   (Integer)    | Weight                                                                              |
|                           | `width`          |                                    |   (Integer)    | Width                                                                               |
|                           | `height`         |                                    |   (Integer)    | Height                                                                              |
|                           | `depth`          |                                    |   (Integer)    | Depth                                                                               |
|                           | `label`          |                                    |    (String)    | Label                                                                               |
| `shipp_company_id`        |                  |                                    |   (Integer)    | Id the carrier in the system                                                        |
| `shipp_company`           |                  |                                    |    (String)    | Shipper                                                                             |
| `estimated_delivery_time` |                  |                                    |     (Date)     | Assumption date of delivery                                                         |
| `total_cost`              |                  |                                    |   (Decimal)    | Total expense                                                                       |
| `cost_by_item`            |                  |                                    |    (Array)     | Costs per individual items                                                          |
|                           | `item_id`        |                                    |   (Integer)    |                                                                                     |
|                           | `name`           |                                    |    (String)    |                                                                                     |
|                           | `price`          |                                    |   (Decimal)    |                                                                                     |
| `order_errors`            |                  |                                    |    (Array)     | Wrong order parameters                                                              |
| `invoice_url`             |                  |                                    | (String/null)  | Order invoice url                                                                   |
| `invoice_id`              |                  |                                    | (Integer/null) | Order invoice id (specific for invoicing system)                                    |     

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
      "order_original_id": "123456",
      "reference_number": "123456",
      "order_id": 654321,
      "status_id": 6,
      "status_name": "is completed",
      "api_update_enabled": false,
      "change_timestamp": "2022-09-12 19:00:54",
      "delivery_id": 291,
      "order_items": [
        {
          "ITEM_ID": 123,
          "COUNT": 1,
          "COUNT_RESERVED": 1
        }
      ],
      "packages": [
        {
          "PACKAGE_NR": "ABC123456",
          "TRACKING_URL": "https://domain.tld/trackandtrace/parcelNumbers=ABC123456",
          "TRACKING_DATA": [
            {
              "timestamp": "2022-09-06 16:25:33",
              "shipment_status": 13,
              "shipment_note": "Undelivered mail - incomplete / not found",
              "shipment_status_delivery_company": "13",
              "shipment_note_delivery_company": "Company name"
            }
          ],
          "IMAGES": {
          },
          "WEIGHT": 624,
          "WIDTH": 410,
          "HEIGHT": 110,
          "DEPTH": 510,
          "LABEL": "https://domain.tld/delivery-labels/2022/09/1662474334_opb_7464753.pdf",
          "package_nr": "ABC123456",
          "tracking_url": "https://domain.tld/trackandtrace/parcelNumbers=ABC123456",
          "tracking_data": [
            {
              "timestamp": "2022-09-06 16:25:33",
              "shipment_status": 13,
              "shipment_note": "Undelivered mail - incomplete / not found",
              "shipment_status_delivery_company": "13",
              "shipment_note_delivery_company": "Company name"
            }
          ],
          "images": {
          },
          "weight": 624,
          "width": 410,
          "height": 110,
          "depth": 510,
          "label": "https://domain.tld/delivery-labels/2022/09/1662474334_opb_7464753.pdf"
        }
      ],
      "shipp_company_id": 291,
      "shipp_company": "Company name",
      "estimated_delivery_time": "2022-09-08",
      "total_cost": 4.89,
      "cost_by_item": [
        {
          "item_id": 11,
          "name": "Picking (unloading) of goods - piece product",
          "price": 0.13
        }
      ],
      "order_errors": {
      },
      "invoice_url": "https://domain.tld/invoices/invoice1.pdf",
      "invoice_id": 123
    }
  }
}
```

[^1]: - mandatory only one of them, `order_id` has a priority if both filled
[^2]: Deprecated, will be removed in the future (use lowercase version instead).
