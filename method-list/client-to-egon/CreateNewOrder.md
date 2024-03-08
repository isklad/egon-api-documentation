# CreateNewOrder

The method inserts a new order into the warehouse system. This method also serves to update orders if a request with an
existing original_order_id is sent to us in the system. In this case, if the order is in the state of 0,1,2,11,12 the
order is updated according to the newly sent data.

## :arrow_forward: Input parameters:

| parameter                    |                  |  format   |                        allowed values                        | mandatory / default value | description                                                                                                                                                                                                                                                                                        |
|:-----------------------------|:-----------------|:---------:|:------------------------------------------------------------:|:-------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `original_order_id`          |                  | (string)  |                              -                               |    :heavy_check_mark:     | Order id from your shop </br>_- Order number from your eshop / system. It is a very important identificator, by which you will be able to find particular order in EGON system. In case you are creating order in EGON manually, you can choose number of your own preference._                    |
| `shop_setting_id`            |                  | (Integer) | [link](https://egon.isklad.eu/klient/settings-shop-settings) |    :heavy_check_mark:     | Set-to-order setting ID                                                                                                                                                                                                                                                                            |
| `business_relationship`      |                  | (String)  |                          b2b / b2c                           |       default: b2c        | Business relationship (b2b/b2c) </br>_- Based on the order designation by the Business Relationship parameter, the system monitors the settings of the goods cards "Block before expiration" or "Block before expiration for B2B" and reserves the goods for the order according to this setting._ |
| `order_type`                 |                  | (String)  |         fulfillment / shipping_label / virtual_order         |   default: fulfillment    | Order type (`fulfillment` - if the whole fulfillment process is managed by EGON, `shipping_label` - if the fulfillment process is managed by an external company, or client himself, `virtual_order` - for notification purposes only)                                                             |
| `reference_number`           |                  | (String)  |                              -                               |           empty           | Reference Nr. of order                                                                                                                                                                                                                                                                             |
| `customer_name`              |                  | (String)  |                              -                               |    :heavy_check_mark:     | Customer - Name                                                                                                                                                                                                                                                                                    |
| `customer_surname`           |                  | (String)  |                              -                               |    :heavy_check_mark:     | Customer - Surname                                                                                                                                                                                                                                                                                 |
| `customer_phone`             |                  | (String)  |                              -                               |    :heavy_check_mark:     | Customer - Phone                                                                                                                                                                                                                                                                                   |
| `customer_email`             |                  | (String)  |                              -                               |    :heavy_check_mark:     | Customer - Email                                                                                                                                                                                                                                                                                   |
| `name`                       |                  | (String)  |                              -                               |    :heavy_check_mark:     | Delivery - Name                                                                                                                                                                                                                                                                                    |
| `surname`                    |                  | (String)  |                              -                               |    :heavy_check_mark:     | Delivery - Surname                                                                                                                                                                                                                                                                                 |
| `phone`                      |                  | (String)  |                              -                               |    :heavy_check_mark:     | Delivery - Phone                                                                                                                                                                                                                                                                                   |
| `email`                      |                  | (String)  |                              -                               |    :heavy_check_mark:     | Delivery - Email                                                                                                                                                                                                                                                                                   |
| `company`                    |                  | (String)  |                              -                               |           empty           | Delivery - Company                                                                                                                                                                                                                                                                                 |
| `street`                     |                  | (String)  |                              -                               |    :heavy_check_mark:     | Delivery - Street                                                                                                                                                                                                                                                                                  |
| `street_number`              |                  | (String)  |                              -                               |    :heavy_check_mark:     | Delivery - Street number                                                                                                                                                                                                                                                                           |
| `entrance_number`            |                  | (String)  |                              -                               |           empty           | Delivery - Entrance number                                                                                                                                                                                                                                                                         |
| `door_number`                |                  | (String)  |                              -                               |           empty           | Delivery - Door number                                                                                                                                                                                                                                                                             |
| `city`                       |                  | (String)  |                              -                               |    :heavy_check_mark:     | Delivery - City                                                                                                                                                                                                                                                                                    |
| `county`                     |                  | (String)  |                              -                               |           empty           | Delivery - District of delivery address (Romania, etc.)                                                                                                                                                                                                                                            |
| `country`                    |                  | (String)  |                              -                               |    :heavy_check_mark:     | Delivery - Country                                                                                                                                                                                                                                                                                 |
| `postal_code`                |                  | (String)  |                              -                               |    :heavy_check_mark:     | Delivery - ZIP code                                                                                                                                                                                                                                                                                |
| `fa_company`                 |                  | (String)  |                              -                               |           empty           | Billing - Company                                                                                                                                                                                                                                                                                  |
| `fa_street`                  |                  | (String)  |                              -                               |           empty           | Billing - Street                                                                                                                                                                                                                                                                                   |
| `fa_street_number`           |                  | (String)  |                              -                               |           empty           | Billing - Street number                                                                                                                                                                                                                                                                            |
| `fa_city`                    |                  | (String)  |                              -                               |           empty           | Billing - City                                                                                                                                                                                                                                                                                     |
| `fa_country`                 |                  | (String)  |                              -                               |           empty           | Billing - Country                                                                                                                                                                                                                                                                                  |
| `fa_postal_code`             |                  | (String)  |                              -                               |           empty           | Billing - ZIP code                                                                                                                                                                                                                                                                                 |
| `fa_ico`                     |                  | (String)  |                              -                               |           empty           | Billing - ID                                                                                                                                                                                                                                                                                       |
| `fa_dic`                     |                  | (String)  |                              -                               |           empty           | Billing - Tax registration number                                                                                                                                                                                                                                                                  |
| `fa_icdph`                   |                  | (String)  |                              -                               |           empty           | Billing - VAT ID                                                                                                                                                                                                                                                                                   |
| `auto_process`               |                  | (Integer) |                            0 / 1                             |             0             | Whether the order is to be held or processed (not a required parameter)                                                                                                                                                                                                                            |
| `on_label`                   |                  | (String)  |                              -                               |           empty           | The name of the sender on the shipping label                                                                                                                                                                                                                                                       |
| `gps_lat`                    |                  | (String)  |                              -                               |           empty           | Latitude                                                                                                                                                                                                                                                                                           |
| `gps_long`                   |                  | (String)  |                              -                               |           empty           | Longitude                                                                                                                                                                                                                                                                                          |
| `note`                       |                  | (String)  |                              -                               |           empty           | Note                                                                                                                                                                                                                                                                                               |
| `currency`                   |                  | (String)  |                              -                               |           empty           | Currency                                                                                                                                                                                                                                                                                           |
| `destination_country_code`   |                  | (String)  |           [link](../../code-lists/country-list.md)           |           empty           | Country ID                                                                                                                                                                                                                                                                                         |
| `id_delivery`                |                  | (Integer) |       [link](../../code-lists/transport-type-list.md)        |    :heavy_check_mark:     | Transport ID                                                                                                                                                                                                                                                                                       |
| `delivery_branch_id`         |                  | (Integer) |       [link](../../code-lists/transport-type-list.md)        |           empty           | Pickup point ID                                                                                                                                                                                                                                                                                    |
| `external_branch_id`         |                  | (String)  |     [link](../../code-lists/transport-type-list.md)[^1]      |           empty           | Pickup point ID from an external company (e.g., Packeta)                                                                                                                                                                                                                                           |
| `default_tax`                |                  | (Decimal) |                              -                               |           empty           | default TAX %                                                                                                                                                                                                                                                                                      |
| `id_payment`                 |                  | (Integer) |       [link](../../code-lists/payment-method-list.md)        |           empty           | ID payment                                                                                                                                                                                                                                                                                         |
| `payment_cod`                |                  | (Integer) |                            0 / 1                             |    :heavy_check_mark:     | Payment - Cash on Delivery                                                                                                                                                                                                                                                                         |
| `cod_price_without_tax`      |                  | (Decimal) |                              -                               |           empty           | Amount in Cash excluding VAT                                                                                                                                                                                                                                                                       |
| `cod_price`                  |                  | (Decimal) |                            - [^2]                            |           empty           | Amount in Cash including VAT                                                                                                                                                                                                                                                                       |
| `deposit_without_tax`        |                  | (Decimal) |                              -                               |           empty           | Advance Payment excluding VAT                                                                                                                                                                                                                                                                      |
| `deposit`                    |                  | (Decimal) |                              -                               |           empty           | Advance including VAT                                                                                                                                                                                                                                                                              |
| `delivery_price_without_tax` |                  | (Decimal) |                              -                               |           empty           | Shipping price excluding VAT                                                                                                                                                                                                                                                                       |
| `delivery_price`             |                  | (Decimal) |                              -                               |           empty           | Shipping price including VAT                                                                                                                                                                                                                                                                       |
| `payment_price_without_tax`  |                  | (Decimal) |                              -                               |           empty           | Price for payment excluding VAT                                                                                                                                                                                                                                                                    |
| `payment_price`              |                  | (Decimal) |                              -                               |           empty           | Price for payment including VAT                                                                                                                                                                                                                                                                    |
| `discount_price_without_tax` |                  | (Decimal) |                              -                               |           empty           | Discount on items excluding VAT                                                                                                                                                                                                                                                                    |
| `discount_price`             |                  | (Decimal) |                              -                               |           empty           | Discount on items including VAT                                                                                                                                                                                                                                                                    |
| `min_delivery_date`          |                  | (String)  |                              -                               |           empty           | Earliest delivery date (Y-m-d)                                                                                                                                                                                                                                                                     |
| `items`                      |                  |  (Array)  |                              -                               |    :heavy_check_mark:     | Item fields                                                                                                                                                                                                                                                                                        |
|                              | `item_id`        | (Integer) |                              -                               |    :heavy_check_mark:     | Internal ID cards                                                                                                                                                                                                                                                                                  |
|                              | `catalog_id`     | (String)  |                              -                               |           empty           | Catalog number                                                                                                                                                                                                                                                                                     |
|                              | `name`           | (String)  |                              -                               |    :heavy_check_mark:     | Product name                                                                                                                                                                                                                                                                                       |
|                              | `count`          | (Integer) |                              -                               |    :heavy_check_mark:     | Quantity                                                                                                                                                                                                                                                                                           |
|                              | `expiration`     | (Integer) |                            0 / 1                             |             0             | Order with expiration                                                                                                                                                                                                                                                                              |
|                              | `exp_value`      | (String)  |                              -                               |           empty           | Expiration date \[YYYY-MM-DD-, YYYY-MM, YYYY\]                                                                                                                                                                                                                                                     |
|                              | `price`          | (Decimal) |                              -                               |           empty           | Price excluding VAT                                                                                                                                                                                                                                                                                |
|                              | `price_with_tax` | (Decimal) |                              -                               |           empty           | Price including VAT                                                                                                                                                                                                                                                                                |
|                              | `tax`            | (Decimal) |                              -                               |           empty           | TAX %                                                                                                                                                                                                                                                                                              |
| `invoice`                    |                  | (Object)  |                              -                               |           empty           | Field of Invoices                                                                                                                                                                                                                                                                                  |
|                              | `invoice_id`     | (Integer) |                              -                               |           empty           | Invoice number                                                                                                                                                                                                                                                                                     |
|                              | `invoice_date`   | (String)  |                              -                               |           empty           | Date of issue (YYYY-MM-DD)                                                                                                                                                                                                                                                                         |
| `invoice_url`                |                  | (String)  |                              -                               |           empty           | Link order invoice in PDF format                                                                                                                                                                                                                                                                   |
| `fa_print`                   |                  | (Integer) |                            0 / 1                             |             0             | PRINT/ PRINT NOT the invoice for shipment                                                                                                                                                                                                                                                          |
| `attachments`                |                  |  (Array)  |                              -                               |           empty           | Attachments to an order                                                                                                                                                                                                                                                                            |
| `packages`                   |                  | (Object)  |                              -                               |                           | Array of packages (mandatory/only for `order_type` = `shipping_label`)                                                                                                                                                                                                                             |
|                              | `weight`         | (Integer) |                              -                               |                           | Weight in grams                                                                                                                                                                                                                                                                                    |

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
    "req_method": "CreateNewOrder",
    "req_data": {
      "original_order_id": 20220608,
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
      "payment_cod": "1",
      "items": [
        {
          "item_id": "1",
          "name": "product name",
          "count": "5"
        }
      ]
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
    "req_method": "CreateNewOrder",
    "req_data": {
      "original_order_id": 202206015,
      "shop_setting_id": 1,
      "business_relationship ": "b2c",
      "reference_number ": "#EAV123",
      "customer_name": "Customer Name",
      "customer_surname": "Customer Surname",
      "customer_phone": "+421 123 567 789",
      "customer_email": "email@domain.tld",
      "name": "Delivery - Name",
      "surname": " Delivery - Surname",
      "phone": "+421 123 567 789",
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
      "fa_company": "Billing - Company",
      "fa_street": "Billing - Street",
      "fa_street_number": "Billing - Street Number",
      "fa_city": "Billing - City",
      "fa_country": "Billing - Country",
      "fa_postal_code": "Billing - ZIP code",
      "fa_ico": "Billing ID",
      "fa_dic": "Billing IDN",
      "fa_icdph": "Billing VAT ID",
      "auto_process": 1,
      "on_label": "MyCompany",
      "gps_lat": "48.142308",
      "gps_long": "17.100281",
      "note": "Note",
      "currency": "EUR",
      "destination_country_code": "SK",
      "id_delivery": "Transport ID",
      "delivery_branch_id": 1,
      "external_branch_id": 1,
      "default_tax": 21,
      "id_payment": 1,
      "payment_cod": 0,
      "cod_price_without_tax": 100,
      "cod_price": 121,
      "deposit_without_tax": 10,
      "deposit": 12.1,
      "delivery_price_without_tax": 100,
      "delivery_price": 121,
      "payment_price_without_tax": 10,
      "payment_price": 12.1,
      "discount_price_without_tax": 10,
      "discount_price": 12.1,
      "min_delivery_date": "2022-07-18",
      "items": [
        {
          "item_id": 123,
          "catalog_id": "Water",
          "name": "Product name",
          "count": 1,
          "expiration": 0,
          "exp_value": "2022-08-01",
          "price": 49.59,
          "price_with_tax": 60,
          "tax": 21
        }
      ],
      "invoice": {
        "invoice_id": 123,
        "invoice_date": "2022-08-01"
      },
      "invoice_url": "https://domain.tld/invoice/123",
      "fa_print": 1,
      "attachments": [
        "https://domain.tld/export/docs/orderAttachment1.pdf",
        "https://domain.tld/export/docs/orderAttachment2.pdf"
      ]
    }
  }
}
```

## :arrow_forward: Output parameters:

| parameter      |                     |  format   | description                                                       |
|:---------------|:--------------------|:---------:|:------------------------------------------------------------------|
| `resp_code`    |                     | (Integer) |                                                                   |
| `resp_message` |                     | (String)  |                                                                   |
| `resp_data`    |                     | (Integer) |                                                                   |
|                | `order_id`          | (Integer) | ID of the created order                                           |
|                | `order_status_id`   | (Integer) | Status ID of the created order                                    |
|                | `myorder_url`       | (string)  | Url adress of the created order detail in myorder.isklad.eu       |
|                | `order_status_data` | (string)  | Complete data from the [GetOrderStatus](GetOrderStatus.md) method |

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
      "order_id": 6205572,
      "order_status_id": 0,
      "myorder_url": "https://myorder.isklad.eu/...",
      "order_status_data": "(Full object/data from GetOrderStatus method)"
    }
  }
}
```

[^1]: - mandatory only, if `delivery_branch_id` is not sent  
[^2]: - mandatory only, if `payment_cod` is 1
