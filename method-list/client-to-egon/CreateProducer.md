# CreateProducer

Creates a producer in system.

## :arrow_forward: Input parameters:

| parameter      |     |  format  |              allowed values              | mandatory / default value | description           |
|:---------------|:----|:--------:|:----------------------------------------:|:-------------------------:|:----------------------|
| `name`         |     | (String) |                    -                     |    :heavy_check_mark:     | Producer name         |
| `country_code` |     | (String) | [link](../../code-lists/country-list.md) |    :heavy_check_mark:     | Producer country code |

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
    "req_method": "CreateProducer",
    "req_data": {
      "name": "Producer Name"
    }
  }
}
```

#### Advanced

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    "req_method": "CreateProducer",
    "req_data": {
      "name": "Producer Name",
      "country_code": "SK"
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter      |  format   | description |
|:---------------|:---------:|:------------|
| `PRODUCER_ID ` | (Integer) | Supplier ID |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 401,
  "resp_note": "401: Entry Created",
  "response": {
    "PRODUCER_ID": 4000,
    "resp_code": 401,
    "resp_note": "401: Entry Created"
  }
}
```