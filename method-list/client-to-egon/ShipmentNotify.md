# ShipmentNotify

Method stores (create or update) information about notified shipment

## :arrow_forward: Input parameters:

| parameter            |            |   format   |                        allowed values                        | mandatory / default value | description                                                             |
|:---------------------|:-----------|:----------:|:------------------------------------------------------------:|:-------------------------:|:------------------------------------------------------------------------|
| `shipment_notify_id` |            | (Integer)  |                              -                               |                           | (optional for update) - `shipment_notify_id` return from first response |
| `shop_setting_id`    |            | (Integer)  | [link](https://egon.isklad.eu/klient/settings-shop-settings) |    :heavy_check_mark:     | Set-to-order setting ID                                                 |
| `date_from`          |            | (Datetime) |                              -                               |    :heavy_check_mark:     | Delivery date from                                                      |
| `date_to`            |            | (Datetime) |                              -                               |    :heavy_check_mark:     | Delivery date to                                                        |
| `tracking_number`    |            |  (String)  |                              -                               |    :heavy_check_mark:     | Tracking number                                                         |
| `supplier_id`        |            | (Integer)  |                              -                               |    :heavy_check_mark:     | Supplier ID                                                             |
| `reference_number`   |            |  (String)  |                              -                               |    :heavy_check_mark:     | Reference Nr. of order                                                  |
| `items`              |            |  (Array)   |                              -                               |    :heavy_check_mark:     | Items                                                                   |
|                      | `item_id`  | (Integer)  |                              -                               |    :heavy_check_mark:     | Difference inventory card id                                            |
|                      | `quantity` | (Integer)  |                              -                               |    :heavy_check_mark:     | Difference inventory quantity                                           |

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
    "req_method": "ShipmentNotify",
    "req_data": {
      "shipment_notify_id": 123456,
      "shop_setting_id": 1,
      "date_from": "2022-02-02",
      "date_to": "2022-02-02",
      "tracking_number": "1234567890",
      "supplier_id": 100,
      "reference_number": "ref123",
      "items": [
        {
          "item_id": 1,
          "quantity": 10
        }
      ]
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter            |  format   | description                       |
|:---------------------|:---------:|:----------------------------------|
| `shipment_notify_id` | (integer) | created shipment notification ID  |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 200,
  "resp_note": "200: OK",
  "response": {
    "shipment_notify_id": 123456
  }
}
```

