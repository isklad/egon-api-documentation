# ShipmentNotifyConfirm

The method stores information about the notified shipment

## :arrow_forward: Input parameters:

| parameter               |             | format          | description                                                                                     |
|-------------------------|-------------|-----------------|-------------------------------------------------------------------------------------------------|
| `shipment_notify_id`    |             | (integer)       | Notification ID, previously received from [ShipmentNotify](../client-to-egon/ShipmentNotify.md) |
| `shipment_arrived_at`   |             | (datetime/null) | Shipment receive date                                                                           |
| `shipment_confirmed_at` |             | (datetime/null) | Date of comparison (after pairing of all product cards)                                         |
| `items`                 |             | (array)         | List of received goods                                                                          |
|                         | `item_id`   | (integer)       | received inventory card id                                                                      |
|                         | `quantity`  | (integer)       | received inventory quantity                                                                     |
| `items_notified`        |             | (array)         | List of pre-advised items                                                                       |
|                         | `item_id`   | (integer)       | advised inventory card id                                                                       |
|                         | `quantity`  | (integer)       | advised inventory quantity                                                                      |
| `differences`           |             | (array)         | The difference between the received and notified list of goods                                  |
|                         | `item_id`   | (integer)       | difference inventory card id                                                                    |
|                         | `quantity`  | (integer)       | difference inventory quantity                                                                   |

### Sample request

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY"
  },
  "request": {
    "req_method": "ShipmentNotifyConfirm",
    "req_data": {
      "shipment_notify_id": 1,
      "shipment_arrived_at": "2021-01-01 12:31",
      "shipment_confirmed_at": null,
      "items": {
        "item_id": 1,
        "quantity": 10
      },
      "items_notified": {
        "item_id": 1,
        "quantity": 15
      },
      "differences": {
        "item_id": 1,
        "quantity": -5
      }
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