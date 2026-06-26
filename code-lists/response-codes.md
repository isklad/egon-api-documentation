# Response and error codes

Every API response contains two independent status fields:

- `auth_status` — the result of **authentication** (see the table below).
- `resp_code` — the result of the **requested method** (see the table below).

## :arrow_forward: CLIENT -> EGON

### - `auth_status` codes:

| code | description   | note                                                        |
|------|---------------|-------------------------------------------------------------|
| 201  | Auth Accepted | API accepted client authentication                          |
| 202  | Unauthorized  | API refused client authentication - incorrect data was sent |
| 301  | Bad Request   | Authentication data is missing or has a wrong structure     |

### - `resp_code` codes:

| code | description        | note                                                                     |
|------|--------------------|--------------------------------------------------------------------------|
| 200  | OK                 | Default response code when the method does not set a more specific one    |
| 301  | Bad Request        | Data in the request does not match the required structure                |
| 302  | Method Not Found   | The method in the request was not found                                  |
| 303  | Method Not Allowed | The requested method is not allowed (e.g. disabled in your API settings)  |
| 401  | Entry Created      | The record was successfully created                                      |
| 402  | Entry Updated      | The record was successfully updated                                      |
| 403  | Content Found      | The requested content was found and returned                             |
| 404  | Content Not Found  | Requested content not found                                              |
| 429  | Too Many Requests  | Request rate limit reached (also returned as HTTP status 429)            |
| 500  | Unexpected error   | An unexpected error occurred on the API side                             |

> :information_source: Codes `201` / `202` belong to `auth_status` (see the table above), not to `resp_code`.
> The HTTP status code of the response also carries meaning: `401` when `auth_status` is `202` (Unauthorized),
> `429` when the rate limit is reached, `403` when the account/API is disabled, otherwise `200`.

## :arrow_forward: EGON-> CLIENT

### - `resp_status` codes:

| code | description | note                                                                                                          |
|------|-------------|---------------------------------------------------------------------------------------------------------------|
| 0    | ERROR       | when an error has occurred - we recommend a specific error logging yourself and alerting IT department to it. |
| 1    | OK          | when the request was accepted without errors                                                                  |
