# InventoryStatusUpdate

Request to update stock inventories in client's software. Egon fires it everytime when inventory card is changed.

## Input parameters

Data is created by associative field of inventory cards, where key is the ID of inventory card from client system and value is
field with data for this inventory card.

| parameter                                                                                       |            | format    | descripton                                                            |
|-------------------------------------------------------------------------------------------------|------------|-----------|-----------------------------------------------------------------------|
| `ITEM_ID`                                                                                       |            | (integer) | inventory card ID in client system                                    |
| `CATALOG_ID`                                                                                    |            | (string)  | Catalog number                                                        |
| `EAN`                                                                                           |            | (string)  | inventory card EAN                                                    |
| `ESHOP_ID`                                                                                      |            | (integer) | eshop ID, to which the card belongs                                   |
| ~~`COUNT`~~ ![deprecated](../../assets/images/deprecated.png)[^1]                               |            | (integer) | = ALL - RESERVED - EXPIRED - DAMAGED                                  |
| ~~`COUNT_INCLUDED_RESERVED`~~ ![deprecated](../../assets/images/deprecated.png)[^1]             |            | (integer) | = ALL - EXPIRED - DAMAGED                                             |
| ~~`RESERVED_FOR_ORDERS`~~ ![deprecated](../../assets/images/deprecated.png)[^1]                 |            | (integer) | = RESERVED                                                            |
| ~~`DAMAGED`~~ ![deprecated](../../assets/images/deprecated.png)[^1]                             |            | (integer) | = DAMAGED                                                             |
| ~~`ORDERED`~~ ![deprecated](../../assets/images/deprecated.png)[^1]                             |            | (integer) | = ORDERED                                                             |
| ~~`AVAILABLE_INCL_RESERVED_AND_ORDERED`~~ ![deprecated](../../assets/images/deprecated.png)[^1] |            | (integer) | = ALL - EXPIRED - DAMAGED + ORDERED                                   |
| `PURCHASE_PRICE`                                                                                |            | (decimal) | Last known buying price of product, if not available, value is 'null' |
| `WITH_VAT`                                                                                      |            | (integer) | Parameter, if price is with VAT                                       |
| `COUNT_TYPES`                                                                                   |            | (array)   | count types wrapper, list of possible count types                     |
|                                                                                                 | `ALL`      | (integer) | Counts of all item physically on stock (for accounting purposes)      |
|                                                                                                 | `EXPIRED`  | (integer) | Count of expired                                                      |
|                                                                                                 | `DAMAGED`  | (integer) | Count of damaged                                                      |
|                                                                                                 | `ORDERED`  | (integer) | Count of ordered                                                      |
|                                                                                                 | `RESERVED` | (integer) | Count of reserved                                                     |

![recommended](../../assets/images/recommended.png) formulas: 

- display on shop: `ALL` - `EXPIRED` - `DAMAGED` - `ORDERED` - `RESERVED`
- accounting purposes: `ALL`

### Sample request

```json
{
  "req_method": "InventoryStatusUpdate",
  "req_data": {
    "123456": {
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
        "RESERVED": 21
      }
    }
  }
}
```

[^1]: deprecated, will be removed in the future