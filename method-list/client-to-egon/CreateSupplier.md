# CreateSupplier

Creates supplier in system

# _Ktore paraemetre su povinne_

## Input parameters:

| parameter             |     |  format   | allowed values |                mandatory                 | description                        |
|:----------------------|:----|:---------:|:--------------:|:----------------------------------------:|:-----------------------------------|
| `name`                |     | (String)  |                |            :heavy_check_mark:            | Supplier - Name                    |
| `auto_shipment_load ` |     | (Integer) |     0 / 1      |                                          | Load shipments automatically       |
| `country_code`        |     | (String)  |                | [link](../../code-lists/country-list.md) | Supplier - Country code            |
| `delivery_days`       |     | (String)  |                |                                          | Delivery time for goods (days)     |
| `vat_payer`           |     | (Integer) |     0 / 1      |                                          | VAT payer                          |
| `street`              |     | (String)  |                |                                          | Supplier - Street                  |
| `street_number`       |     | (String)  |                |                                          | Supplier - Street number           |
| `postal_code`         |     | (String)  |                |                                          | Supplier - ZIP code                |
| `city `               |     | (String)  |                |                                          | Supplier - City                    |
| `ico`                 |     | (String)  |                |                                          | Supplier - Company ID              |
| `dic`                 |     | (String)  |                |                                          | Supplier - Tax registration number |
| `ic_dph`              |     | (String)  |                |                                          | Supplier - VAT ID                  |
| `email_orders`        |     | (String)  |                |                                          | Email for orders                   |
| `email_info`          |     | (String)  |                |                                          | Email for info                     |
| `tax_rate`            |     | (Decimal) |                |                                          | VAT amount in %                    |

## Sample request

### Minimal

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
    "req_method": "CreateSupplier",
    "req_data": {
      "name": "Supplier Name",
      "auto_shipment_load": 0,
      "country_code": "SK",
      "delivery_days": " ",      
      "vat_payer": 0,
      "street": "Supplier - Street",
      "street_number": "Supplier - Street number",
      "postal_code": "Supplier - Postal code",
      "city": "Supplier - City",
      "ico": "Supplier - Company ID",
      "dic": "Supplier - Tax registration number",
      "ic_dph": "Supplier - VAT ID",
      "email_orders": "supplier@mail.com",
      "email_info": "supplier@mail.com",
      "tax_rate": 20
    }
  }
}
```

### Advanced

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY",
    "auth_token": "AUTH_TOKEN"
  },
  "request": {
  }
}
```

# _doplnit parametre a response_

## Output parameters:

| parameter      |     |   format    | description |
|----------------|-----|:-----------:|-------------|
| `SUPPLIER_ID ` |     | ( Integer ) | Supplier ID |

## Sample response

```json
{
  
  
  
  
}
```