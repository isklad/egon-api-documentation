<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/images/logo_white.png">
  <img alt="logo" src="assets/images/logo_black.png">
</picture>

# Documentation for the RestAPI v1 client

The API Client Web Service ("API") is intended for [isklad.eu](https://isklad.eu) clients who need to transfer data
between their information
system (e-commerce) and isklad.eu's information system via this service.

The API is implemented on isklad.eu and is accessible via the Internet. Provides a set of methods for exchanging storage
card data, orders, shipping methods, payments, invoices, etc ...

The isklad.eu project is constantly developing and the set of methods is being continuously complemented by other new
services. For this reason, the most up-to-date version of this documentation, which is provided by your isklad.eu
merchant, is necessary to implement.

The documentation contains a detailed description of each available method with the following details:

- Description of input parameters and their values
- Example request
- Sample Response

## Integration manual: CLIENT-> EGON

The interface works on the Request / Response principle over the HTTP protocol. Sending page - Client information system
can be a desktop application, a web portal, a database application, and so on. with internet access.

The interface is available at: [https://api.isklad-egon.sk/rest/v1](https://api.isklad-egon.sk/rest/v1)

:bulb: Sklad API Connector - PHP package for API communication -> Available for download here:
[https://github.com/zoltanlaca/isklad-api-connector](https://github.com/zoltanlaca/isklad-api-connector)

The client's information system initiates communication by sending a request in a defined format and returns a JSON
response. The `GET` / `POST` method is used.

:warning: The limit on the number of requests per client (based on `auth_id`) is: 180 req / min

### Sample request

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

### Sample Response

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

## Integration manual: EGON-> CLIENT

### Interface description

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

#### Basic description of the call

Each request from the warehouse system will contain the correct authentication data and the query
itself (`POST` parameter `req`). The authentication data is unique and will be provided to you by your trader
(they are the same as the data that you verify when requesting a warehouse system - without `auth_token`)

#### Sample request

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

#### Sample response
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