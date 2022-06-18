# ShipmentNotifyConfirm

The method stores information about the notified shipment

## Input parameters
| parameter               |             | format          | description                                                                                     |
|-------------------------|-------------|-----------------|-------------------------------------------------------------------------------------------------|
| `shipment_notify_id`    |             | (integer)       | Notification ID, previously received from [ShipmentNotify](../client-to-egon/ShipmentNotify.md) |
| `shipment_arrived_at`   |             | (datetime)      | Shipment receive date                                                                           |
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

```json
{
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
```