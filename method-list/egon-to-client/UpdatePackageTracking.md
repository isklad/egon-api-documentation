# UpdatePackageTracking

Request to update tracking statuses for respective package/ shipment.

## :arrow_forward: Input parameters:

Associative field with info about package.

| parameter           |                                    | format         | description                                                                                                 |
|---------------------|------------------------------------|----------------|-------------------------------------------------------------------------------------------------------------|
| `order_id`          |                                    | (Integer/null) | Order ID in EGON                                                                                            |
| `original_order_id` |                                    | (String/null)  | Order ID in Eshop                                                                                           |
| `box_packing_id`    |                                    | (Integer)      | Parcel ID in EGON                                                                                           |
| `package_nr`        |                                    | (String)       | Shipment number                                                                                             |
| `tracking_data`     |                                    | (Array)        | Field with data from tracking                                                                               |
|                     | `timestamp`                        | (Datetime)     | Time of status change (if shipper does not provide this data, it will be the time of status change in EGON) |
|                     | `shipment_status`                  | (Integer)      | Status ID from index                                                                                        |
|                     | `shipment_note`                    | (String)       | status name from index                                                                                      |
|                     | `shipment_status_delivery_company` | (String)       | Status ID of shipping company                                                                               |
|                     | `shipment_note_delivery_company`   | (String)       | Status name of shipping company                                                                             |
| `tracking_url`      |                                    | (String)       | Tracking url                                                                                                |

### Sample request

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY"
  },
  "request": {
    "req_method": "UpdatePackageTracking",
    "req_data": {
      "box_packing_id": 123456,
      "package_nr": "ABC123456",
      "tracking_data": [
        {
          "timestamp": "2022-08-24 16:39:05",
          "shipment_status": 2,
          "shipment_note": "Carrier accepted the shipment",
          "shipment_status_delivery_company": "received",
          "shipment_note_delivery_company": "Company name "
        },
        {
          "timestamp": "2022-08-24 18:51:16",
          "shipment_status": 4,
          "shipment_note": "Shipment is being delivered",
          "shipment_status_delivery_company": "transit",
          "shipment_note_delivery_company": "Company name "
        }
      ],
      "tracking_url": "https://domain.tld/ABC123456",
      "order_id": 987654,
      "original_order_id": "654321"
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
```