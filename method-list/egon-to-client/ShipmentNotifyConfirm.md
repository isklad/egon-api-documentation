# ShipmentNotifyConfirm

The method stores information about the notified shipment

## :arrow_forward: Input parameters:

| parameter               |                          | format          | description                                                                                     |
|-------------------------|--------------------------|-----------------|-------------------------------------------------------------------------------------------------|
| `shipment_notify_id`    |                          | (integer)       | Notification ID, previously received from [ShipmentNotify](../client-to-egon/ShipmentNotify.md) |
| `shipment_arrived_at`   |                          | (datetime/null) | Shipment receive date                                                                           |
| `shipment_confirmed_at` |                          | (datetime/null) | Date of comparison (after pairing of all product cards)                                         |
| `items`                 |                          | (array)         | List of received goods                                                                          |
|                         | `warehouse_inventory_id` | (integer)       | received warehouse inventory card id                                                            |
|                         | `inventory_id`           | (integer/null)  | received inventory card id                                                                      |
|                         | `ean`                    | (string)        | received inventory ean                                                                          |
|                         | `item_id`                | (integer/null)  | received inventory card item_id                                                                 |
|                         | `count`                  | (integer)       | received inventory quantity                                                                     |
| `items_notified`        |                          | (array)         | List of pre-advised items                                                                       |
|                         | `inventory_id`           | (integer/null)  | advised inventory card id                                                                       |
|                         | `item_id`                | (integer/null)  | advised inventory card item_id                                                                  |
|                         | `ean`                    | (string/null)   | advised ean                                                                                     |
|                         | `count`                  | (integer)       | advised inventory quantity                                                                      |
| `differences`           |                          | (array)         | The difference between the received and notified list of goods                                  |
|                         | `warehouse_inventory_id` | (integer/null)  | difference warehouse inventory card id                                                          |
|                         | `inventory_id`           | (integer/null)  | difference inventory card id                                                                    |
|                         | `item_id`                | (integer)       | difference inventory card item_id                                                               |
|                         | `ean`                    | (string/null)   | difference ean                                                                                  |
|                         | `count`                  | (integer)       | difference inventory quantity                                                                   |
|                         | `countNotified`          | (integer)       | difference inventory quantity notified                                                          |
|                         | `difference`             | (integer)       | difference quantity                                                                             |
| `paired_packages`       |                          | (array)         | List of paired packages/items                                                                   |
|                         | `package_id`             | (integer)       | package ID                                                                                      |
|                         | `package_box_id`         | (integer)       | package box ID                                                                                  |

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
      "items": [
        {
          "warehouse_inventory_id": 1,
          "inventory_id": null,
          "ean": "1234567890123",
          "item_id": null,
          "count": 10
        }
      ],
      "items_notified": [
        {
          "inventory_id": 1,
          "item_id": 1,
          "ean": null,
          "count": 15
        }
      ],
      "differences": [
        {
          "warehouse_inventory_id": 1,
          "inventory_id": 1,
          "item_id": 1,
          "ean": null,
          "count": 10,
          "countNotified": 15,
          "difference": -5
        }
      ],
      "paired_packages": [
        {
          "package_id": 1,
          "package_box_id": 1
        }
      ]
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