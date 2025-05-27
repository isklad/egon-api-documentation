# Integration manual: CLIENT-> EGON

The interface works on the Request / Response principle over the HTTP protocol. Sending page - Client information system
can be a desktop application, a web portal, a database application, and so on with internet access.

The interface is available at: [https://api.isklad.com/rest/v1](https://api.isklad.com/rest/v1)

:bulb: iSklad API Connector - PHP package for API communication -> Available for download here:
[https://github.com/zoltanlaca/isklad-api-connector](https://github.com/zoltanlaca/isklad-api-connector)

The client's information system initiates communication by sending a request in a defined format and returns a JSON
response. The `GET` / `POST` method is used.

:warning: The limit on the number of requests per client (based on `auth_id`) is: 180 req / min

## :arrow_forward: Input parameters:

Input data encoded in JSON format (RAW):

| parameter |              |  format  | mandatory / default value | description                                        |
|:----------|--------------|:--------:|:-------------------------:|:---------------------------------------------------|
| `auth`    |              | (array)  |    :heavy_check_mark:     | your private identifier keys to sign in to the API |
|           | `auth_id`    | (string) |    :heavy_check_mark:     | these identifiers are provided by the merchant     |
|           | `auth_key`   | (string) |    :heavy_check_mark:     | these identifiers are provided by the merchant     |
|           | `auth_token` | (string) |    :heavy_check_mark:     | these identifiers are provided by the merchant     |
| `request` |              | (array)  |    :heavy_check_mark:     | request wrapper                                    |
|           | `req_method` | (string) |    :heavy_check_mark:     | call method, e.g. `CreateNewOrder`                 |
|           | `req_data`   | (array)  |    :heavy_check_mark:     | call parameters, value depends on called method    |

Endpoint: [https://api.isklad.com/rest/v1](https://api.isklad.com/rest/v1) (RAW JSON)

### Sample request

The call field must be encoded into JSON format and sent to the API via POST methods.

The sample call looks like this:

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    "req_method": "MethodName",
    "req_data": {
      "param1": 1,
      "param2": 2
    }
  }
}
```

## :arrow_forward: Output parameters:

Data obtained in response by decoding JSON format:

| parameter             |         |  format   | description                             |
|:----------------------|:--------|:---------:|:----------------------------------------|
| `auth_status`         |         | (integer) | the result code of the authorization    |
| `auth_status_message` |         | (string)  | the result message of the authorization |
| `resp_code`           |         | (string)  | response code                           |
| `resp_note`           |         | (string)  | message based on `resp_code`            |
| `response`            |         |  (array)  | response wrapper                        |
|                       | `error` | (string)  | optional error message                  |

:bulb: The response codes correspond to the code in
the [Response and error codes](../code-lists/response-codes.md#--resp_code-codes)
section.

## Sample Response

The sample answer in the JSON format looks like this:

```json
{
  "auth_status": 301,
  "auth_status_message": "301: Bad Request",
  "resp_code": 200,
  "resp_note": "200: OK",
  "response": {
    "error": "Param [/auth] is mandatory, missing in this request."
  }
}
```

