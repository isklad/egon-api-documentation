# InventoryCardAttachmentList

List all product label attachments belonging to a single inventory card.

## :arrow_forward: Input parameters:

| parameter |  |  |   format   | allowed values |     mandatory      | description                                           |
|:----------|--|--|:----------:|:--------------:|:------------------:|:------------------------------------------------------|
| `item_id` |  |  | (Integer)  |       -        | :heavy_check_mark: | Inventory card item ID (the client's item identifier) |

### Sample request

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    "req_method": "InventoryCardAttachmentList",
    "req_data": {
      "item_id": 123456
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter     |                |  |   format   | description                                                              |
|:--------------|:---------------|--|:----------:|:-------------------------------------------------------------------------|
| `attachments` |                |  |  (Array)   | List of attachments for the inventory card                               |
|               | `id`           |  | (Integer)  | Attachment ID (use with `InventoryCardAttachmentDelete`)                 |
|               | `name`         |  |  (String)  | Original file name of the uploaded PDF                                   |
|               | `type`         |  | (Integer)  | [Attachment (label) type](../../code-lists/attachment-type-list.md) ID   |
|               | `country_code` |  |  (String)  | Destination [country code](../../code-lists/country-list.md) (e.g. `SK`) |
|               | `enabled`      |  | (Boolean)  | Whether the attachment is enabled                                        |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 403,
  "resp_note": "403: Content Found",
  "response": {
    "resp_code": 403,
    "resp_message": "403: Content Found",
    "resp_data": {
      "attachments": [
        {
          "id": 9876,
          "name": "label-sk.pdf",
          "type": 1,
          "country_code": "SK",
          "enabled": true
        },
        {
          "id": 9877,
          "name": "label-cz.pdf",
          "type": 1,
          "country_code": "CZ",
          "enabled": false
        }
      ]
    }
  }
}
```

When the inventory card has no attachments, an empty list is returned with the `404: Content Not Found` response code.

### Error responses

A `301: Bad Request` is returned in the following cases:

- Missing or invalid `item_id`
- Inventory card not found for the given `item_id`
