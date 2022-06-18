# CreateOrderReturnLabel

Creates a return label for packages that are returned from the customer to the warehouse

## Input parameters:

| parameter         |     | format         | mandatory               | description                                                                       |
|-------------------|-----|----------------|-------------------------|-----------------------------------------------------------------------------------|
| order_id          |     | (integer/null) | :heavy_check_mark: [^1] | order id from egon (previously received from [CreateNewOrder](CreateNewOrder.md)) |
 | original_order_id |     | (string/null)  | :heavy_check_mark: [^1] | order id from your shop (previously passed to [CreateNewOrder](CreateNewOrder.md))                     |
| box_count         |     | (integer)      | :heavy_check_mark:      | number of packages we want to generate a label for                                |
| email_send        |     | (boolean)      | :heavy_check_mark:      | if we want send an email with info to customer set it to true                     |

[^1]: - mandatory only one of them, `order_id` has a priority if both filled

## Sample request

```json
{
  "req_method": "CreateOrderReturnLabel",
  "req_data": {
    "order_id": 132,
    "original_order_id": 321,
    "box_count": 2,
    "email_send": false
  }
}
```

## Output parameters:

| parameter       |                     | format    | description                            |
|-----------------|---------------------|-----------|----------------------------------------|
| `return_labels` |                     | (array)   | created labels wrapper                 |
|                 | `id`                | (integer) | id of the generated return label       |
|                 | `barcode`           | (string)  | barcode of the generated return label  |
|                 | `label_pdf_base64`  | (string)  | base64 encoded PDF file                |


## Sample response
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
        "label_pdf_base64": "base64string...."
      },
      {
        "id": 2,
        "barcode": "xy1232",
        "label_pdf_base64": "base64string...."
      }
    ]
  }
}
```