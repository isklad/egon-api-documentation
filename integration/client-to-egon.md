# Integration manual: CLIENT-> EGON

The interface works on the Request / Response principle over the HTTP protocol. Sending page - Client information system
can be a desktop application, a web portal, a database application, and so on. with internet access.

The interface is available at: [https://api.isklad-egon.sk/rest/v1](https://api.isklad-egon.sk/rest/v1)

:bulb: Sklad API Connector - PHP package for API communication -> Available for download here:
[https://github.com/zoltanlaca/isklad-api-connector](https://github.com/zoltanlaca/isklad-api-connector)

The client's information system initiates communication by sending a request in a defined format and returns a JSON
response. The `GET` / `POST` method is used.

:warning: The limit on the number of requests per client (based on `auth_id`) is: 180 req / min

## Sample request

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

The call field must be encoded into JSON format and sent to the API via POST methods.

Input data encoded in JSON format (RAW):

| parameter     |                 | format   | description                                          |
|---------------|-----------------|----------|------------------------------------------------------|
| `auth`        |                 | (array)  | your private identifier keys to sign in to the API   |
|               | `auth_id`       | (string) | these identifiers are provided by the merchant       |
|               | `auth_key`      | (string) | these identifiers are provided by the merchant       |
|               | `auth_token`    | (string) | these identifiers are provided by the merchant       |
| `request`     |                 | (array)  | request wrapper                                      |
|               | `req_method`    | (string) | call method, e.g. `CreateNewOrder`                   |
|               | `req_data`      | (array)  | call parameters, value depends on called method      |

Inbound url:
[https://api.isklad-egon.sk/rest/v1](https://api.isklad-egon.sk/rest/v1) (RAW JSON)

## Sample Response

```json
{
  "auth_status": "OK",
  "response": {
    "resp_code": 200,
    "resp_note": "OK",
    "resp_data": {
      "param1": 1,
      "param2": 2
    }
  }
}
```

The sample answer in the JSON format looks like this:

| parameter      |              | format    | description                             |
|----------------|--------------|-----------|-----------------------------------------|
| `auth_status`  |              | (string)  | the result message of the authorization |
| `response`     |              | (array)   | response wrapper                        |
|                | `resp_code`  | (string)  | response code                           |
|                | `resp_note`  | (string)  | message based on `resp_code`            |
|                | `resp_data`  | (array)   | response data based on called method    |

:bulb: The error codes correspond to the code in the "error codes" section.