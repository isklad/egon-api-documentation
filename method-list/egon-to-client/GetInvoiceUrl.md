# GetInvoiceUrl

Request to return an Invoice to Order.

## :arrow_forward: Input parameters:

Associative field with info about package.

| parameter           |     | format         | description       |
|---------------------|-----|----------------|-------------------|
| `order_id`          |     | (Integer/null) | Order ID in EGON  |
| `original_order_id` |     | (String/null)  | Order ID in Eshop |
| `change_timestamp ` |     | (Datetime)     | Parcel ID in EGON |

### Sample request

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY"
  },
  "request": {
    "req_method": "GetInvoiceUrl",
    "req_data": {
      "order_original_id": "123456",
      "order_id": 789654,
      "change_timestamp": "2019-09-13 11:19:49"
    }
  }
}
```

## :arrow_forward: Output parameters:

Data obtained by decoding JSON format:

| parameter     |               | format    | description                          |
|---------------|---------------|-----------|--------------------------------------|
| `auth_status` |               | (Integer) | the result code of the authorization |
| `response`    |               | (Array)   | response wrapper                     |
|               | `resp_status` | (Integer) | response code                        |
|               | `invoice_url` | (String)  | Invoice url                          |

:bulb: The response codes correspond to the code in
the [Response and error codes](../../code-lists/response-codes.md#--resp_status-codes)
section.

### Sample response

The sample answer in the JSON format looks like this:

```json
{
  "auth_status": 1,
  "response": {
    "resp_status": 1,
    "invoice_url": "https://domain.tld/inovice/invoice01.pdf"
  }
}
```