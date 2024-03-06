# CreatePackage ![deprecated](../../assets/images/deprecated.png)

Method is DEPRECATED and will be removed in the future.
Use the `CreateNewOrder` method instead (with `order_type` = `external`);

The method inserts a parcel into the system (sending without fulfillment).

## :arrow_forward: Input parameters:

| parameter                  |          |    format    |                          allowed values                          | mandatory / default value | description                                                                        |
|:---------------------------|:---------|:------------:|:----------------------------------------------------------------:|:-------------------------:|:-----------------------------------------------------------------------------------|
| `original_order_id`        |          |   (string)   |                                -                                 |    :heavy_check_mark:     | Order id from your shop (previously passed to [CreateNewOrder](CreateNewOrder.md)) |
| `shop_setting_id`          |          |  (Integer)   |   [link](https://egon.isklad.eu/klient/settings-shop-settings)   |    :heavy_check_mark:     | Set-to-order setting ID                                                            |
| `reference_number`         |          |   (String)   |                                -                                 |           empty           | Reference Nr. of order                                                             |
| `customer_name`            |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Customer - Name                                                                    |
| `customer_surname`         |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Customer - Surname                                                                 |
| `customer_phone`           |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Customer - Phone                                                                   |
| `customer_email`           |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Customer - Email                                                                   |
| `name`                     |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Delivery - Name                                                                    |
| `surname`                  |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Delivery - Surname                                                                 |
| `phone`                    |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Delivery - Phone                                                                   |
| `email`                    |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Delivery - Email                                                                   |
| `company`                  |          |   (String)   |                                -                                 |           empty           | Delivery - Company                                                                 |
| `street`                   |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Delivery - Street                                                                  |
| `street_number`            |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Delivery - Street number                                                           |
| `entrance_number`          |          |   (String)   |                                -                                 |           empty           | Delivery - Entrance number                                                         |
| `door_number`              |          |   (String)   |                                -                                 |           empty           | Delivery - Door number                                                             |
| `city`                     |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Delivery - City                                                                    |
| `county`                   |          |   (String)   |                                -                                 |           empty           | Delivery - District of delivery address (Romania, etc.)                            |
| `country`                  |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Delivery - Country                                                                 |
| `postal_code`              |          |   (String)   |                                -                                 |    :heavy_check_mark:     | Delivery - ZIP code                                                                |
| `on_label`                 |          |   (String)   |                                -                                 |           empty           | The name of the sender on the shipping label                                       |
| `gps_lat`                  |          |   (String)   |                                -                                 |           empty           | Latitude                                                                           |
| `gps_long`                 |          |   (String)   |                                -                                 |           empty           | Longitude                                                                          |
| `note`                     |          |   (String)   |                                -                                 |           empty           | Note                                                                               |
| `currency`                 |          |   (String)   |                                -                                 |           empty           | Currency                                                                           |
| `destination_country_code` |          |   (String)   |             [link](../../code-lists/country-list.md)             |           empty           | Country ID                                                                         |
| `id_delivery`              |          |  (Integer)   |         [link](../../code-lists/transport-type-list.md)          |    :heavy_check_mark:     | Transport ID                                                                       |
| `delivery_branch_id`       |          |  (Integer)   |         [link](../../code-lists/transport-type-list.md)          |           empty           | Pickup point ID                                                                    |
| `external_branch_id`       |          |   (String)   |                               [^1]                               |           empty           | Pickup point ID from an external company (e.g., Packeta)                           |
| `id_payment`               |          |  (Integer)   |         [link](../../code-lists/payment-method-list.md)          |           empty           | ID payment                                                                         |
| `payment_cod`              |          |  (Integer)   |                              0 / 1                               |    :heavy_check_mark:     | Payment - Cash on Delivery                                                         |
| `cod_price_without_tax`    |          |  (Decimal)   |                                -                                 |           empty           | Amount in Cash excluding VAT                                                       |
| `cod_price`                |          |  (Decimal)   |                              - [^2]                              |           empty           | Amount in Cash including VAT                                                       |
| `cod_to_iban`              |          |   (String)   |                              - [^3]                              |           empty           | IBAN, for which a payout will be sent                                              |
| `cod_to_swift`             |          |   (String)   |                              - [^3]                              |           empty           | SWIFT to IBAN above                                                                |
| `min_delivery_date`        |          |   (String)   |                                -                                 |           empty           | Earliest delivery date (year-month) - if not completed as soon as possible         |
| `packages`                 |          |   (Object)   |                                -                                 |    :heavy_check_mark:     |                                                                                    |
|                            | `weight` |  (Decimal)   |                                -                                 |    :heavy_check_mark:     | Weight in grams                                                                    |

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
    "req_method": "CreatePackage",
    "req_data": {
      "original_order_id": 123456,
      "shop_setting_id": 1,
      "customer_name": "Customer Name",
      "customer_surname": "Customer Surname",
      "customer_phone": "+421123567789",
      "customer_email": "email@domain.tld",
      "name": "Delivery - Name",
      "surname": " Delivery - Surname",
      "phone": "+421123567789",
      "email": "delivery@mail.com",
      "street": "Delivery - Street",
      "street_number": "Delivery - Street Number ",
      "city": "Delivery - City",
      "country": "Delivery - Country",
      "postal_code": "Delivery - ZIP code",
      "id_delivery": "Transport ID",
      "payment_cod": 0,
      "packages": {
        "1": {
          "weight": 500
        }
      }
    }
  }
}
```

#### Advanced

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    "req_method": "CreatePackage",
    "req_data": {
      "original_order_id": 123456,
      "shop_setting_id": 1,
      "reference_number ": "#EAV123",
      "customer_name": "Customer Name",
      "customer_surname": "Customer Surname",
      "customer_phone": "+421123567789",
      "customer_email": "email@domain.tld",
      "name": "Delivery - Name",
      "surname": " Delivery - Surname",
      "phone": "+421123567789",
      "email": "delivery@mail.com",
      "company": "Delivery - Company",
      "street": "Delivery - Street",
      "street_number": "Delivery - Street Number ",
      "entrance_number": "Delivery - Entrance Number",
      "door_number": "Delivery - Door Number",
      "city": "Delivery - City",
      "county": "Alba",
      "country": "Delivery - Country",
      "postal_code": "Delivery - ZIP code",
      "on_label": "MyCompany",
      "gps_lat": "48.142308",
      "gps_long": "17.100281",
      "note": "Note",
      "currency": "EUR",
      "destination_country_code": "SK",
      "id_delivery": "Transport ID",
      "delivery_branch_id": 1,
      "external_branch_id": 1,
      "id_payment": 1,
      "payment_cod": 0,
      "cod_price_without_tax": 100,
      "cod_price": 121,
      "cod_to_iban": 121,
      "cod_to_swift": 121,
      "min_delivery_date": 121,
      "packages": {
        "1": {
          "weight": 500
        }
      }
    }
  }
}

```

## :arrow_forward: Output parameters:

| parameter  |  format  | description |
|:-----------|:--------:|:------------|
| `order_id` | (string) | Order ID    |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 401,
  "resp_note": "401: Entry Created",
  "response": {
    "resp_code": 401,
    "resp_message": "401: Entry Created",
    "resp_data": {
      "order_id": 6363474
    }
  }
}
```

[^1]: - mandatory only, if `delivery_branch_id` is not sent     
[^2]: - mandatory only, if `payment_cod` is 1  
[^3]: - `cod_to_iban` and `code_to_swift` do not need to complete. If they are not filled, this data is affected by the
default account setup (based on `shop_setting_id`).