# WriteOrderStatus

Request to write an order status to the client system.

## :arrow_forward: Input parameters:


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
| `invoice_id`              |                  |                                    | (Integer/null) | Order invoice id (specific for invoicing system)                                    |                                     |

### Sample request

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY"
  },
  "request": {
    "req_method": "WriteOrderStatus",
    "req_data": {
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

## :arrow_forward: Output parameters:

Data obtained by decoding JSON format:

| parameter     |               | format    | description                          |
|---------------|---------------|-----------|--------------------------------------|
| `auth_status` |               | (integer) | the result code of the authorization |
| `response`    |               | (array)   | response wrapper                     |
|               | `resp_status` | (integer) | response code                        |

:bulb: The response codes correspond to the code in
the [Response and error codes](../../code-lists/response-codes.md#--resp_status-codes)
section.

### Sample response

The sample answer in the JSON format looks like this:

```json
{
  "auth_status": 1,
  "response": {
    "resp_status": 1
  }
}
