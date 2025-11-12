# MyOrderClaimUpdate

Request to trigger the update of the claim status in the client's system.

## :arrow_forward: Input parameters:

| parameter |             |                     |        |     format     | description                                              |
|:----------|:------------|:--------------------|:-------|:--------------:|:---------------------------------------------------------|
| `claim`   |             |                     |        |    (Object)    | The claim object                                         |
|           | `id`        |                     |        |   (Integer)    | Claim ID                                                 |
|           | `status`    |                     |        |    (Object)    | Claim status object                                      |
|           |             | `id`                |        |   (integer)    | Claim status ID [Status list](../../code-lists/myorder_claim_statuses.md) |
|           |             | `name`              |        |    (String)    | Claim status name                                        |
|           | `order`     |                     |        |    (Object)    | Order object                                             |
|           |             | `id`                |        |   (integer)    | Order ID                                                 |
|           |             | `original_order_id` |        |    (String)    | Original order id (from the client's system)             |
|           | `delivery`  |                     |        |    (Object)    | Delivery object                                          |
|           |             | `id`                |        |   (integer)    | Delivery ID                                              |
|           |             | `name`              |        |    (String)    | Delivery name                                            |
|           |             | `branch`            |        | (Object/null)  | Delivery branch object                                   |
|           |             |                     | `id`   |   (Integer)    | Delivery branch ID                                       |
|           |             |                     | `name` |    (String)    | Delivery branch name                                     |
|           | `bank`      |                     |        |    (Object)    | Bank account object                                      |
|           |             | `iban`              |        | (String/null)  | Customers bank account IBAN                              |
|           |             | `swift`             |        | (String/null)  | Customers bank account SWIFT                             |
|           |             | `name`              |        | (String/null)  | Customers bank account name                              |
|           | `packages`  |                     |        |    (Array)     | Package array                                            |
|           |             | `id`                |        |   (Integer)    | Package ID                                               |
|           |             | `awb`               |        |    (String)    | Package AWB (barcode)                                    |
|           |             | `password`          |        | (String/null)  | Package password                                         |
|           |             | `label`             |        | (String/null)  | Package label url address                                |
|           | `prices`    |                     |        |    (Object)    | Prices object                                            |
|           |             | `currency`          |        |    (String)    | Prices currency                                          |
|           |             | `goods`             |        |    (Float)     | Price sum of the claimed items                           |
|           |             | `delivery`          |        |    (Float)     | Price of the delivery (from order)                       |
|           |             | `refund`            |        |    (Float)     | Price of the claim refund                                |
|           | `items`     |                     |        |    (Array)     | Claimed items array                                      |
|           |             | `id`                |        |   (Integer)    | Claim item ID                                            |
|           |             | `item_id`           |        | (Integer/null) | Item ID from the client inventory                        |
|           |             | `catalog_id`        |        | (String/null)  | Catalog ID from the client inventory                     |
|           |             | `name`              |        | (String/null)  | Name ID from the client inventory                        |
|           |             | `quantity`          |        |   (Integer)    | Quantity of the returned items                           |
|           |             | `description`       |        |    (String)    | Returned items description                               |
|           |             | `price`             |        |    (Float)     | Returned items price                                     |
|           |             | `return_type`       |        |    (Object)    | Returned type object                                     |
|           |             |                     | `id`   |   (Integer)    | Returned type ID                                         |
|           |             |                     | `name` |    (String)    | Returned type name                                       |
| `history` |             |                     |        |    (Array)     | Array of the status history entries                      |
|           | `status_id` |                     |        |   (Integer)    | Status id of the history entry                           |
|           | `timestamp` |                     |        |   (DateTime)   | Datetime of the history entry (Y-m-d H:i:s)              |
|           | `note`      |                     |        |    (String)    | Note of the history entry                                |

### Sample request

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY"
  },
  "request": {
    "req_method": "MyOrderClaimUpdate",
    "req_data": {
      "claim": {
        "id": 1,
        "status": {
          "id": 1,
          "name": "Created"
        },
        "order": {
          "id": 1,
          "original_order_id": "1234567890"
        },
        "delivery": {
          "id": 1,
          "name": "Delivery name",
          "branch": {
            "id": 10,
            "name": "Branch name"
          }
        },
        "bank": {
          "iban": null,
          "swift": null,
          "name": "Bank account name"
        },
        "packages": [
          {
            "id": 1,
            "awb": "123456789012",
            "password": null,
            "label": "https://domain.tld/label.pdf"
          }
        ],
        "prices": {
          "currency": "EUR",
          "goods": 100.02,
          "delivery": 0.00,
          "refund": 1.50
        },
        "items": [
          {
            "id": 1,
            "item_id": 100,
            "catalog_id": "123456789012",
            "name": "Item name",
            "quantity": 1,
            "description": "Item description",
            "price": 100.02,
            "return_type": {
              "id": 1,
              "name": "Return"
            }
          }
        ]
      },
      "history": [
        {
          "status_id": 1,
          "timestamp": "2024-02-24 02:24:20",
          "note": "Claim created"
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
