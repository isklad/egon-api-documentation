# Integration manual: EGON-> CLIENT

## Interface description

For the proper functionality and collaboration of the client and warehouse system, it is necessary to create a feedback
channel towards the client system. It is necessary to integrate the options when the EGON warehouse system sends
information
about the performance of an operation (packing, shipping, etc.) and in the client system it records the order for the
order,
the stock card, etc.

The interface works on the Request / Response principle over the HTTP protocol. The sending party is the EGON storage
system.

The interface should be available at URL: http://domena-klienta.sk/cesta-k-api/

The EGON storage system initiates communication by sending a request in a specified format and returns a JSON response.
The GET / POST method is used.

### Basic description of the call

Each request from the warehouse system will contain the correct authentication data and the query
itself (`POST` parameter `req`). The authentication data is unique and will be provided to you by your trader
(they are the same as the data that you verify when requesting a warehouse system - without `auth_token`)

### Sample request

The call fields will send the stock system encoded into JSON format via the `POST` method.
Find input data encoded in JSON format under the param `req`.

The sample call looks like this:

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY"
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

| parameter     |                 | format      | description                                           |
|---------------|-----------------|-------------|-------------------------------------------------------|
| `auth`        |                 | (array)     | your private identifier keys to sign in to the API    |
|               | `auth_id`       | (string)    | these identifiers are provided by the merchant        |
|               | `auth_key`      | (string)    | these identifiers are provided by the merchant        |
| `request`     |                 | (array)     | request wrapper                                       |
|               | `req_method`    | (string)    | call method, e.g. `WriteOrderStatus`                  |
|               | `req_data`      | (array)     | call parameters, value depends on called method       |


Inbound link, e.g.: https://your-domain.tld/path-to-isklad-listener, read data from `req` param and decode it from JSON.

### Sample response
The sample answer in the JSON format looks like this:


```json
{
  "auth_status": 201,
  "response": {
    "resp_status": 200
  }
}
```
Data obtained by decoding JSON format:

| parameter     |              | format    | description                          |
|---------------|--------------|-----------|--------------------------------------|
| `auth_status` |              | (integer) | the result code of the authorization |
| `response`    |              | (array)   | response wrapper                     |
|               |`resp_status` | (integer) | response code                        |

:bulb: The error codes correspond to the code in the "error codes" section.