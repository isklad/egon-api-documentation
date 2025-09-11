# CreateOrderReturnLabel ![deprecated](/assets/images/deprecated.png)

Creates a return label for packages that are returned from the customer to the warehouse

## :arrow_forward: Input parameters:

| parameter           |     |     format     | allowed values | mandatory / default value | description                                                                        |
|:--------------------|:----|:--------------:|:--------------:|:-------------------------:|:-----------------------------------------------------------------------------------|
| `order_id `         |     | (integer/null) |       -        |  :heavy_check_mark: [^1]  | Order id from egon (previously received from [CreateNewOrder](CreateNewOrder.md))  |
| `original_order_id` |     | (string/null)  |       -        |  :heavy_check_mark: [^1]  | Order id from your shop (previously passed to [CreateNewOrder](CreateNewOrder.md)) |
| `box_count`         |     |   (integer)    |       -        |    :heavy_check_mark:     | Number of packages we want to generate a label for                                 |
| `email_send `       |     |   (boolean)    |       -        |    :heavy_check_mark:     | If we want send an email with info to customer set it to true                      |

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
    "req_method": "CreateOrderReturnLabel",
    "req_data": {
      "order_id": 132,
      "original_order_id": 321,
      "box_count": 2,
      "email_send": false
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter       |                    |  format   | description                             |
|:----------------|:-------------------|:---------:|:----------------------------------------|
| `return_labels` |                    |  (array)  | created labels wrapper                  |
|                 | `id`               | (integer) | id of the generated return label        |
|                 | `barcode`          | (string)  | barcode of the generated return label   |
|                 | `password`         | (string)  | password for the generated return label |
|                 | `tracking_url`     | (string)  | url for display tracking status         |
|                 | `label_pdf_base64` | (string)  | base64 encoded PDF file                 |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 401,
  "resp_note": "401: Entry Created",
  "response": {
    "return_labels": [
      {
        "id": 1,
        "barcode": "xy1231",
        "password": "ABC",
        "tracking_url": "https://tracking-domain.tld/example",
        "label_pdf_base64": "base64string...."
      },
      {
        "id": 2,
        "barcode": "xy1232",
        "password": "ABC",
        "tracking_url": "https://tracking-domain.tld/example",
        "label_pdf_base64": "base64string...."
      }
    ]
  }
}
```

[^1]: - mandatory only one of them, `order_id` has a priority if both filled