# Integration manual: EGON-> CLIENT

## Interface description

For the proper functionality and collaboration of the client and warehouse system, it is necessary to create a feedback
channel towards the client system. It is necessary to integrate the options when the EGON warehouse system sends
information
about the performance of an operation (packing, shipping, etc.) and in the client system it records the order for the
order,
the stock card, etc.

The interface works on the Request / Response principle over the HTTP protocol. The sending party is the EGON warehouse
system.

The interface should be available at URL: "https://domain.tld/api/

The EGON warehouse system initiates communication by sending a request in a specified format and returns a JSON response.
The `GET` / `POST` method is used.

### Basic description of the call

Each request from the warehouse system will contain the correct authentication data and the query
itself (`POST` parameter `req`). The authentication data is unique and will be provided to you by your trader
(they are the same as the data that you verify when requesting a warehouse system - without `auth_token`)

## :arrow_forward: Input parameters:

Input data encoded in JSON format (RAW):

| parameter |              |  format  | mandatory / default value | description                                        |
|:----------|--------------|:--------:|:-------------------------:|:---------------------------------------------------|
| `auth`    |              | (array)  |    :heavy_check_mark:     | your private identifier keys to sign in to the API |
|           | `auth_id`    | (string) |    :heavy_check_mark:     | these identifiers are provided by the merchant     |
|           | `auth_key`   | (string) |    :heavy_check_mark:     | these identifiers are provided by the merchant     |
| `request` |              | (array)  |    :heavy_check_mark:     | request wrapper                                    |
|           | `req_method` | (string) |    :heavy_check_mark:     | call method, e.g. `WriteOrderStatus`               |
|           | `req_data`   | (array)  |    :heavy_check_mark:     | call parameters, value depends on called method    |

Endpoint url, e.g.: https://your-domain.tld/path-to-isklad-listener, read data from `req` param and decode it from JSON.

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

## :arrow_forward: Output parameters:

Data obtained by decoding JSON format:

| parameter     |               | format    | description                          |
|---------------|---------------|-----------|--------------------------------------|
| `auth_status` |               | (integer) | the result code of the authorization |
| `response`    |               | (array)   | response wrapper                     |
|               | `resp_status` | (integer) | response code                        |

:bulb: The response codes correspond to the code in
the [Response and error codes](../code-lists/response-codes.md#--resp_status-codes)
section.

### Sample response

The sample answer in the JSON format looks like this:

```json
{
  "auth_status": 1,
  "response": {
    "resp_status": 1
  }
}
```