# ChangeClaimStatus

Change status of a MyOrder claim.

## :arrow_forward: Input parameters:

| parameter |          |      |  format   | allowed values |     mandatory      | description                                             |
|:----------|:---------|------|:---------:|:--------------:|:------------------:|:--------------------------------------------------------|
| `claim`   |          |      | (object)  |       -        | :heavy_check_mark: |                                                         |
|           | `id`     |      | (integer) |       -        | :heavy_check_mark: | ID of MyOrder claim.                                    | 
|           | `status` |      | (object)  |       -        | :heavy_check_mark: |                                                         | 
|           |          | `id` | (integer) |      `4`       | :heavy_check_mark: | ID of new status. Allowed new statuses: `4` -  refunded | 

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
    "req_method": "ChangeClaimStatus",
    "req_data": {
      "claim": {
        "id": 1,
        "status": {
          "id": 4
        }
      }
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter |              |        |  format   | description                      |
|:----------|:-------------|--------|:---------:|:---------------------------------|
| `claim`   |              |        | (object)  |                                  |
|           | `id`         |        | (integer) | ID of MyOrder claim.             | 
|           | `updated_at` |        | (string)  | Time of update of MyOrder claim. | 
|           | `status`     |        | (object)  |                                  | 
|           |              | `id`   | (integer) | ID of new status.                | 
|           |              | `name` | (string)  | Name of new status.              | 

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 402,
  "resp_note": "402: Entry Updated",
  "response": {
    "resp_code": 402,
    "resp_message": "402: Entry Updated",
    "resp_data": {
      "success": true,
      "claim": {
        "id": 1,
        "updated_at": "2024-05-06 14:11:33",
        "status": {
          "id": 4,
          "name": "Refunded"
        }
      }
    }
  }
}
```
