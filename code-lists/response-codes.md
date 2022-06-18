# Response and error codes

| code | description          | note                                                        |
|------|----------------------|-------------------------------------------------------------|
| 201  | Auth Accepted        | API accepted client authentication                          |
| 202  | Unauthorized         | API refused client authentication - incorrect data was sent |
| 301  | Bad Request          | Data in the requester does not match the required structure |
| 302  | Method Not Found     | The method in the request was not found                     |
| 303  | Method Not Allowed   | The request in the request is not allowed                   |
| 401  | Entry Created        | The recording was successfully created                      |
| 402  | Entry Updated        | The recording was successfully edited                       |
| 403  | Content Found        | The requested content was found and returned                |
| 404  | Content Not Found    | Requested content not found                                 |