# PackingOptions

Sends back information about packaging options.

## :arrow_forward: Input parameters:

| parameter |     | format | allowed values | mandatory / default value | description |
|:----------|:----|:------:|:--------------:|:-------------------------:|:------------|
|           |     |        |                |                           |             |

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
    "req_method": "PackingOptions",
    "req_data": []
  }
}


```

## :arrow_forward: Output parameters:

| parameter    |         |            |  format   | description                 |
|:-------------|:--------|:-----------|:---------:|:----------------------------|
| `CATEGORIES` |         |            |  (Array)  |                             |
|              | `ID`    |            | (Integer) | Category ID                 |
|              | `NAME`  |            | (String)  | Category name               |
|              | `BOXES` |            |  (Array)  | Catalog nr.                 |
|              |         | `ID`       | (Integer) | Packaging ID                |
|              |         | `NAME`     | (String)  | Packaging name              |
|              |         | `WIDTH`    | (Integer) | Packaging width             |
|              |         | `HEIGHT`   | (Integer) | Packaging height            |
|              |         | `WEIGHT`   | (Integer) | Packaging weight            |
|              |         | `LAYERS`   | (Integer) | Number of packaging layers  |
|              |         | `MAX_LOAD` | (Integer) | Maximal load of packaging   |
|              |         | `PRICE`    | (Decimal) | Packaging price             |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 200,
  "resp_note": "200: OK",
  "response": {
    "CATEGORIES": [
      {
        "ID": 7,
        "NAME": "5 layer",
        "BOXES": [
          {
            "ID": 8,
            "NAME": "Cardboard 5VL 300/200/200",
            "WIDTH": 200,
            "HEIGHT": 200,
            "WEIGHT": 242,
            "LAYERS": 5,
            "MAX_LOAD": 6500,
            "PRICE": 0.4
          }
        ]
      }
    ],
    "resp_code": 200,
    "resp_note": "200: OK"
  }
}
```
