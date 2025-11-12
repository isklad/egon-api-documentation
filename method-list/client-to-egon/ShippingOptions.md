# ShippingOptions

Sends back info about shipping companies and costs.

## :arrow_forward: Input parameters:

| parameter      |     |     format     | allowed values | mandatory / default value | description         |
|:---------------|:----|:--------------:|:--------------:|:-------------------------:|:--------------------|
| `delivery_id ` |     | (integer/null) |       -        |    :heavy_check_mark:     | Shipping company ID |

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
    "req_method": "ShippingOptions",
    "req_data": {
      "delivery_id": 6
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter                    |                        |                         |    format     | description                                                                             |
|:-----------------------------|:-----------------------|:------------------------|:-------------:|:----------------------------------------------------------------------------------------|
| `ID`                         |                        |                         |   (Integer)   | Shipping company ID                                                                     |
| `NAME`                       |                        |                         |   (String)    | Shipping option name                                                                    |
| `IMAGE`                      |                        |                         |   (String)    | Picture of shipping option                                                              |
| `COD_AVAILABILITY`           |                        |                         |   (Integer)   | COD availability                                                                        |
| `CARD_PAYMENT_AVAILABILITY ` |                        |                         |   (Integer)   | Credit card payment possibility                                                         |
| `TRANSFER_TYPE `             |                        |                         |   (Integer)   | Shipping type                                                                           |
| `TRANSFER_TYPE_NAME `        |                        |                         |   (String)    | Shipping type name                                                                      |
| `CUT_OFF_TIMES `             |                        |                         |    (Array)    |                                                                                         |
| `COD_TRANSFER_DAYS `         |                        |                         |   (Integer)   | Number of days to receive COD                                                           |
|                              | `TIME`                 |                         |   (String)    | Cutoff time for the order to be sent on the same day                                    |
| `COUNTRIES `                 |                        |                         |    (Array)    |                                                                                         |
|                              | `ID`                   |                         |   (Integer)   | Country ID                                                                              |
|                              | `CODE`                 |                         |   (String)    | Country code                                                                            |
|                              | `NAME_SK`              |                         |   (String)    | Country name SK                                                                         |
|                              | `NAME_EN`              |                         |   (String)    | Country name EN                                                                         |
|                              | `NAME_DE`              |                         |   (String)    | Country name DE                                                                         |
|                              | `DELIVERY_DAYS `       |                         |   (Integer)   | Delivery days                                                                           |
| `BRANCHES`                   |                        |                         |    (Array)    |                                                                                         |
|                              | `ID`                   |                         |   (Integer)   | Pickup point ID                                                                         |
|                              | `EXTERNAL_ID `         |                         |   (Integer)   | Pickup point external ID                                                                |
|                              | `NAME`                 |                         |   (String)    | Pickup point name                                                                       |
|                              | `STREET`               |                         |   (String)    | Pickup point street                                                                     |
|                              | `STREET_NUMBER`        |                         | (String/null) | Pickup point street number                                                              |
|                              | `POSTAL_CODE`          |                         |   (String)    | Pickup point ZIP code                                                                   |
|                              | `CITY `                |                         |   (String)    | Pickup point city                                                                       |
|                              | `GPS_LAT `             |                         |   (String)    | GPS LAT of pickup point                                                                 |
|                              | `GPS_LONG `            |                         |   (String)    | GPS LONG of pickup point                                                                |
|                              | `PACKET_CONSIGNMENT  ` |                         |   (Integer)   | Return transfer                                                                         |
|                              | `IN_OPERATION  `       |                         |   (Integer)   | operation status of parcelshops or lockers, e.g. if the locker is full, status may be 0 |
| `PRICES`                     |                        |                         |   (Object)    |                                                                                         |
|                              | `WEIGHT_UNIT`          |                         |   (String)    | Weight unit                                                                             |
|                              | `PRICE_UNIT`           |                         |   (String)    | Price unit                                                                              |
|                              | `BY_WEIGHT`            |                         |    (Array)    |                                                                                         |
|                              |                        | `FROM`                  |   (Integer)   | Weight category from                                                                    |
|                              |                        | `TO`                    |   (Integer)   | Weight category from                                                                    |
|                              |                        | `PRICE`                 |   (Decimal)   | Price of weight category                                                                |
|                              | `BY_COD`               |                         |    (Array)    |                                                                                         |
|                              |                        | `FROM`                  |   (Integer)   | COD sum from                                                                            |
|                              |                        | `TO`                    |   (Integer)   | COD sum from                                                                            |
|                              |                        | `PRICE`                 |   (Decimal)   | Price for COD                                                                           |
|                              | `BY_SERVICE `          |                         |   (Object)    |                                                                                         |
|                              |                        | `TOLL_FEE`              |   (Decimal)   | Toll fee                                                                                |
|                              |                        | `TYPE_OF_TOLL_FEE`      |   (Integer)   | Toll fee type                                                                           |
|                              |                        | `TYPE_OF_TOLL_FEE_NAME` |   (String)    | Toll fee type name                                                                      |
|                              |                        | `FUEL_FEE`              |   (Integer)   | Fuel fee                                                                                |
|                              |                        | `FUEL_FEE_UNIT`         |   (String)    | Fuel fee unit                                                                           |
|                              |                        | `CARD_FEE`              |   (Integer)   | Card payment fee                                                                        |
|                              |                        | `CARD_FEE_UNIT`         |   (String)    | Fee unit for card card payment                                                          |
|                              |                        | `OVERSIZE_FEE `         |   (Integer)   | Fee for oversize                                                                        |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 200,
  "resp_note": "200: OK",
  "response": {
    "0": {
      "ID": 6,
      "NAME": "Supplier name",
      "IMAGE": "https://domain.tld/img1.jpg",
      "COD_AVAILABILITY": 1,
      "CARD_PAYMENT_AVAILABILITY": 1,
      "TRANSFER_TYPE": 1,
      "TRANSFER_TYPE_NAME": "Parcel balíky - pozemná preprava",
      "COUNTRIES": [
        {
          "ID": 203,
          "CODE": "SK",
          "NAME_SK": "Slovenská republika",
          "NAME_EN": "Slovak republic",
          "NAME_DE": "Slowakische Republik",
          "DELIVERY_DAYS": 1
        }
      ],
      "BRANCHES": [],
      "CUT_OFF_TIMES": [
        {
          "TIME": "16:00"
        }
      ],
      "COD_TRANSFER_DAYS": 5,
      "PRICES": {
        "WEIGHT_UNIT": "g",
        "PRICE_UNIT": "EUR",
        "BY_WEIGHT": [
          {
            "FROM": 0,
            "TO": 1000,
            "PRICE": 3
          }
        ],
        "BY_COD": [
          {
            "FROM": 0,
            "TO": 3300,
            "PRICE": 0.7
          }
        ],
        "BY_SERVICE": {
          "TOLL_FEE": 0.02,
          "TYPE_OF_TOLL_FEE": 1,
          "TYPE_OF_TOLL_FEE_NAME": "for each kg (€)",
          "FUEL_FEE": 18,
          "FUEL_FEE_UNIT": "%",
          "CARD_FEE": 1,
          "CARD_FEE_UNIT": "%",
          "OVERSIZE_FEE": 5
        }
      }
    },
    "resp_code": 200,
    "resp_note": "200: OK"
  }
}
```
