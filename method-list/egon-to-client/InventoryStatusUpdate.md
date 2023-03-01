# InventoryStatusUpdate

Request to update stock inventories in client's software. Egon fires it everytime when inventory card is changed.

## :arrow_forward: Input parameters:

Data is created by associative field of inventory cards, where key is the ID of inventory card from client system and
value is field with data for this inventory card.

| parameter                                                                                       |                      |  format   | description                                                           |
|:------------------------------------------------------------------------------------------------|:---------------------|:---------:|:----------------------------------------------------------------------|
| `ID`  |    | (Integer) | inventory card ID in EGON                  |
| `ITEM_ID`                                                                                       |                      | (Integer) | inventory card ID in client system                                    |
| `CATALOG_ID`                                                                                    |                      | (String)  | Catalog number                                                        |
| `EAN`                                                                                           |                      | (String)  | inventory card EAN                                                    |
| `ESHOP_ID`                                                                                      |                      | (Integer) | eshop ID, to which the card belongs                                   |
| ~~`COUNT`~~ ![deprecated](../../assets/images/deprecated.png)[^1]                               |                      | (Integer) | = `ALL` - `RESERVED` - `EXPIRED` - `EXPIRATION_BLOCKED` -`DAMAGED`                          |
| ~~`COUNT_INCLUDED_RESERVED`~~ ![deprecated](../../assets/images/deprecated.png)[^1]             |                      | (Integer) | = `ALL` - `EXPIRED` - `EXPIRATION_BLOCKED` - `DAMAGED`                                       |
| ~~`RESERVED_FOR_ORDERS`~~ ![deprecated](../../assets/images/deprecated.png)[^1]                 |                      | (Integer) | = `RESERVED`                                                          |
| ~~`DAMAGED`~~ ![deprecated](../../assets/images/deprecated.png)[^1]                             |                      | (Integer) | = `DAMAGED`                                                           |
| ~~`ORDERED`~~ ![deprecated](../../assets/images/deprecated.png)[^1]                             |                      | (Integer) | = `ORDERED`                                                           |
| ~~`AVAILABLE_INCL_RESERVED_AND_ORDERED`~~ ![deprecated](../../assets/images/deprecated.png)[^1] |                      | (Integer) | = `ALL` - `EXPIRED` - `EXPIRATION_BLOCKED` - `DAMAGED` + `ORDERED`                           |
| `PURCHASE_PRICE`                                                                                |                      | (Decimal) | Last known buying price of product, if not available, value is 'null' |
| `WITH_VAT`                                                                                      |                      | (Integer) | Parameter, if price is with VAT                                       |
| `COUNT_TYPES` ![recommended](../../assets/images/recommended.png)                               |                      |  (Array)  | count types wrapper, list of possible count types                     |
|                                                                                                 | `ALL`                | (Integer) | Quantity of all items physically on stock (for accounting purposes)   |
|                                                                                                 | `EXPIRED`            | (Integer) | Quantity of expired items                                             |
|                                                                                                 | `DAMAGED`            | (Integer) | Quantity of damaged items                                             |
|                                                                                                 | `ORDERED`            | (Integer) | Quantity of ordered items                                             |
|                                                                                                 | `RESERVED`           | (Integer) | Quantity of reserved items                                            |
|                                                                                                 | `EXPIRATION_BLOCKED` | (Integer) | Quantity of blocked items by expiration, but not expired yet          |

> **![recommended](../../assets/images/recommended.png) formulas:**
> - display on shop: `ALL` - `EXPIRED` - `EXPIRATION_BLOCKED` - `DAMAGED` - `ORDERED` - `RESERVED`
> - accounting purposes: `ALL`

### Sample request

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY"
  },
  "request": {
    "req_method": "InventoryStatusUpdate",
    "req_data": {
      "123456": {
        "ID": 123,
        "ITEM_ID": "123456",
        "CATALOG_ID": "abc",
        "EAN": "123456789012",
        "ESHOP_ID": 108,
        "COUNT": 200,
        "COUNT_INCLUDED_RESERVED": 221,
        "RESERVED_FOR_ORDERS": 21,
        "DAMAGED": 4,
        "ORDERED": 15,
        "AVAILABLE_INCL_RESERVED_AND_ORDERED": 236,
        "PURCHASE_PRICE": 54.45,
        "WITH_VAT": 0,
        "COUNT_TYPES": {
          "ALL": 236,
          "EXPIRED": 2,
          "DAMAGED": 4,
          "ORDERED": 15,
          "RESERVED": 21,
          "EXPIRATION_BLOCKED": 0
        }
      }
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
the [Response and error codes](../../code-lists/response-codes.md#--resp_status-codes)
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

[^1]: Deprecated, will be removed in the future. Use `COUNT_TYPES` with custom formula instead.
