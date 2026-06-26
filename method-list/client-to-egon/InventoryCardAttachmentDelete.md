# InventoryCardAttachmentDelete

Delete a single product label (attachment) from an inventory card by its attachment ID.

## :arrow_forward: Input parameters:

| parameter       |  |  |   format   | allowed values |     mandatory      | description                              |
|:----------------|--|--|:----------:|:--------------:|:------------------:|:-----------------------------------------|
| `attachment_id` |  |  | (Integer)  |       -        | :heavy_check_mark: | ID of the attachment to delete           |

### Sample request

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    "req_method": "InventoryCardAttachmentDelete",
    "req_data": {
      "attachment_id": 9876
    }
  }
}
```

## :arrow_forward: Output parameters:

No `resp_data` is returned. A `402: Entry Updated` response code indicates the attachment was successfully deleted.

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 402,
  "resp_note": "402: Entry Updated",
  "response": {
    "resp_code": 402,
    "resp_message": "402: Entry Updated"
  }
}
```

### Error responses

A `301: Bad Request` is returned in the following cases:

- Missing or invalid `attachment_id`
- The attachment does not exist, or does not belong to the authenticated client
- The attachment could not be deleted
