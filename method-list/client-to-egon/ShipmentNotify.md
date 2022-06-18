# ShipmentNotify

Method stores (create or update) information about notified shipment

## Input parameters

| parameter             |            | format      | mandatory                     | description                                                    |
|-----------------------|------------|-------------|-------------------------------|----------------------------------------------------------------|
| `shipment_notify_id`  |            | (integer)   |                               | (optional for update) - `shipment_notify_id` from first response |
| `shop_setting_id`     |            | (integer)   | :heavy_check_mark:            | Eshop ID                                                       |
| `date_from`           |            | (datetime)  | :heavy_check_mark:            | delivery date from                                             |
| `date_to`             |            | (datetime)  | :heavy_check_mark:            | delivery date to                                               |
| `tracking_number`     |            | (string)    | :heavy_check_mark:            | tracking number                                                |
| `supplier_id`         |            | (integer)   | :heavy_check_mark:            | Supplier ID                                                    |
| `reference_number`    |            | (string)    | :heavy_check_mark:            | reference number                                               |
| `items`               |            | (array)     | :heavy_check_mark:            | items                                                          |
|                       | `item_id`  | (integer)   | :heavy_check_mark:            | difference inventory card id                                   |
|                       | `quantity` | (integer)   | :heavy_check_mark:            | difference inventory quantity                                  |

### Sample request

```json
{
  "req_method": "ShipmentNotify",
  "req_data": {
    "shipment_notify_id": 123465,
    "shop_setting_id": 1,
    "date_from": "2020-02-02",
    "date_to": "2020-02-02",
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
```

## Output parameters

| parameter            | format       | description                       |
|----------------------|--------------|-----------------------------------|
| `shipment_notify_id` | (integer)    | created shipment notification ID  |

## Sample response

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

