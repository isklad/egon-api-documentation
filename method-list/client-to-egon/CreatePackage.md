# CreatePackage

The method inserts a parcel into the system (sending without fulfillment).

## :arrow_forward: Input parameters:

| parameter                  |          |    format     |                        allowed values                        | mandatory / default value | description                                                                        |
|:---------------------------|:---------|:-------------:|:------------------------------------------------------------:|:-------------------------:|:-----------------------------------------------------------------------------------|
| `original_order_id`        |          | (string/null) |                              -                               |    :heavy_check_mark:     | Order id from your shop (previously passed to [CreateNewOrder](CreateNewOrder.md)) |
| `shop_setting_id`          |          |   (Integer)   | [link](https://egon.isklad.eu/klient/settings-shop-settings) |    :heavy_check_mark:     | Set-to-order setting ID                                                            |
| `reference_number`         |          |   (String)    |                              -                               |           empty           | Reference Nr. of order                                                             |
| `customer_name`            |          |   (String)    |                              -                               |    :heavy_check_mark:     | Customer - Name                                                                    |
| `customer_surname`         |          |   (String)    |                              -                               |    :heavy_check_mark:     | Customer - Surname                                                                 |
| `customer_phone`           |          |   (String)    |                              -                               |    :heavy_check_mark:     | Customer - Phone                                                                   |
| `customer_email`           |          |   (String)    |                              -                               |    :heavy_check_mark:     | Customer - Email                                                                   |
| `name`                     |          |   (String)    |                              -                               |    :heavy_check_mark:     | Delivery - Name                                                                    |
| `surname`                  |          |   (String)    |                              -                               |    :heavy_check_mark:     | Delivery - Surname                                                                 |
| `phone`                    |          |   (String)    |                              -                               |    :heavy_check_mark:     | Delivery - Phone                                                                   |
| `email`                    |          |   (String)    |                              -                               |    :heavy_check_mark:     | Delivery - Email                                                                   |
| `company`                  |          |   (String)    |                              -                               |           empty           | Delivery - Company                                                                 |
| `street`                   |          |   (String)    |                              -                               |    :heavy_check_mark:     | Delivery - Street                                                                  |
| `street_number`            |          |   (String)    |                              -                               |    :heavy_check_mark:     | Delivery - Street number                                                           |
| `entrance_number`          |          |   (String)    |                              -                               |           empty           | Delivery - Entrance number                                                         |
| `door_number`              |          |   (String)    |                              -                               |           empty           | Delivery - Door number                                                             |
| `city`                     |          |   (String)    |                              -                               |    :heavy_check_mark:     | Delivery - City                                                                    |
| `county`                   |          |   (String)    |                              -                               |           empty           | Delivery - District of delivery address (Romania, etc.)                            |
| `country`                  |          |   (String)    |                              -                               |    :heavy_check_mark:     | Delivery - Country                                                                 |
| `postal_code`              |          |   (String)    |                              -                               |    :heavy_check_mark:     | Delivery - ZIP code                                                                |
| `on_label`                 |          |   (String)    |                              -                               |           empty           | The name of the sender on the shipping label                                       |
| `gps_lat`                  |          |   (String)    |                              -                               |           empty           | Latitude                                                                           |
| `gps_long`                 |          |   (String)    |                              -                               |           empty           | Longitude                                                                          |
| `note`                     |          |   (String)    |                              -                               |           empty           | Note                                                                               |
| `currency`                 |          |   (String)    |                              -                               |           empty           | Currency                                                                           |
| `destination_country_code` |          |   (String)    |           [link](../../code-lists/country-list.md)           |           empty           | Country ID                                                                         |
| `id_delivery`              |          |   (Integer)   |       [link](../../code-lists/transport-type-list.md)        |    :heavy_check_mark:     | Transport ID                                                                       |
| `delivery_branch_id`       |          |   (Integer)   |       [link](../../code-lists/transport-type-list.md)        |           empty           | Pickup point ID                                                                    |
| `external_branch_id`       |          |   (String)    |                             [^1]                             |           empty           | Pickup point ID from an external company (e.g., Packeta)                           |
| `id_payment`               |          |   (Integer)   |       [link](../../code-lists/payment-method-list.md)        |           empty           | ID payment                                                                         |
| `payment_card`             |          |   (Integer)   |                            0 / 1                             |    :heavy_check_mark:     | Card Payment                                                                       |
| `payment_cod`              |          |   (Integer)   |                         0 / 1  [^2]                          |    :heavy_check_mark:     | Payment - Cash on Delivery                                                         |
| `cod_price_without_tax`    |          |   (Decimal)   |                              -                               |           empty           | Amount in Cash excluding VAT                                                       |
| `cod_price`                |          |   (Decimal)   |                              -                               |           empty           | Amount in Cash including VAT                                                       |
| `cod_to_iban`              |          |   (String)    |                            - [^3]                            |           empty           | IBAN, for which a payout will be sent                                              |
| `cod_to_swift`             |          |   (String)    |                            - [^3]                            |           empty           | SWIFT to IBAN above                                                                |
| `min_delivery_date`        |          |   (String)    |                              -                               |           empty           | Earliest delivery date (year-month) - if not completed as soon as possible         |
| `packages`                 |          |    (Array)    |                              -                               |                           |                                                                                    |
|                            | `weight` |   (Decimal)   |                              -                               |           empty           | Weight in grams                                                                    |


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
      "name": "name"
      
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
    "req_method": "CreateEshopSetting",
    "req_data": {
      "name": "name"
      
    }
  }
}
```
## :arrow_forward: Output parameters:

| parameter  |      |  format  | description |
|:-----------|:-----|:--------:|:------------|
| `order_id` |      | (string) | Order ID    |


### Sample response

```json
{
  
}
```

[^1]: - Only if delivery_branch_id is not sent <br /> 
[^2]: - if 1, cod_price must be filled in <br />
[^3]: - `cod_to_iban` and `code_to_swift` do not need to complete. If they are not filled, this data is affected by the default account setup (based on shop_setting_id).