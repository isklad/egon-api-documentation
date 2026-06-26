# InventoryCardAttachmentCreate

Upload a PDF product label (attachment) to an inventory card for a given destination country. Only **one** attachment can exist per inventory card and country combination.

## :arrow_forward: Input parameters:

| parameter         |  |  |   format   | allowed values |     mandatory      | description                                                                  |
|:------------------|--|--|:----------:|:--------------:|:------------------:|:-----------------------------------------------------------------------------|
| `item_id`         |  |  | (Integer)  |       -        | :heavy_check_mark: | Inventory card item ID (the client's item identifier)                        |
| `attachment_type` |  |  | (Integer)  |       -        | :heavy_check_mark: | [Attachment (label) type](../../code-lists/attachment-type-list.md) ID       |
| `pdf_base64`      |  |  |  (String)  |       -        | :heavy_check_mark: | The PDF file content, base64 encoded. Must be a valid PDF                     |
| `pdf_name`        |  |  |  (String)  |       -        | :heavy_check_mark: | Original file name of the PDF                                                 |
| `country_code`    |  |  |  (String)  |       -        | :heavy_check_mark: | Destination [country code](../../code-lists/country-list.md) (e.g. `SK`)     |

### Sample request

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    "req_method": "InventoryCardAttachmentCreate",
    "req_data": {
      "item_id": 123456,
      "attachment_type": 1,
      "pdf_base64": "JVBERi0xLjcKJ...==",
      "pdf_name": "label-sk.pdf",
      "country_code": "SK"
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter       |  |  |   format   | description                          |
|:----------------|--|--|:----------:|:-------------------------------------|
| `attachment_id` |  |  | (Integer)  | ID of the newly created attachment   |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 401,
  "resp_note": "401: Entry Created",
  "response": {
    "resp_code": 401,
    "resp_message": "401: Entry Created",
    "resp_data": {
      "attachment_id": 9876
    }
  }
}
```

### Error responses

A `301: Bad Request` is returned in the following cases:

- Missing or invalid required parameters
- Invalid `country_code` (unknown or not available to the client)
- Invalid `attachment_type` (unknown or disabled)
- Inventory card not found for the given `item_id`
- Invalid PDF format / failed to store the attachment
- An attachment already exists for this inventory card and country combination — in this case the existing attachment ID is returned in `resp_data.attachment_id`

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 301,
  "resp_note": "301: Bad Request",
  "response": {
    "resp_code": 301,
    "resp_message": "Attachment already exists for this combination (inventory and country)",
    "resp_data": {
      "attachment_id": 9876
    }
  }
}
```
