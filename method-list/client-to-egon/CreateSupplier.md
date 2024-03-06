# CreateSupplier

Creates supplier in system. If the `ICO` parameter is filled, the system checks if the supplier already exists. If the supplier exists, the system updates the supplier. 
If the supplier does not exist, the system creates a new supplier.

## :arrow_forward: Input parameters:

| parameter             |     |  format   |              allowed values              | mandatory / default value | description                        |
|:----------------------|:----|:---------:|:----------------------------------------:|:-------------------------:|:-----------------------------------|
| `name`                |     | (String)  |                    -                     |    :heavy_check_mark:     | Supplier - Name                    |
| `auto_shipment_load ` |     | (Integer) |                  0 / 1                   |    :heavy_check_mark:     | Load shipments automatically       |
| `country_code`        |     | (String)  | [link](../../code-lists/country-list.md) |    :heavy_check_mark:     | Supplier - Country code            |
| `delivery_days`       |     | (String)  |                    -                     |           empty           | Delivery time for goods (days)     |
| `vat_payer`           |     | (Integer) |                  0 / 1                   |             0             | VAT payer                          |
| `street`              |     | (String)  |                    -                     |           empty           | Supplier - Street                  |
| `street_number`       |     | (String)  |                    -                     |           empty           | Supplier - Street number           |
| `postal_code`         |     | (String)  |                    -                     |           empty           | Supplier - ZIP code                |
| `city `               |     | (String)  |                    -                     |           empty           | Supplier - City                    |
| `ico`                 |     | (String)  |                    -                     |           empty           | Supplier - Company ID              |
| `dic`                 |     | (String)  |                    -                     |           empty           | Supplier - Tax registration number |
| `ic_dph`              |     | (String)  |                    -                     |           empty           | Supplier - VAT ID                  |
| `email_orders`        |     | (String)  |                    -                     |           empty           | Email for orders                   |
| `email_info`          |     | (String)  |                    -                     |           empty           | Email for info                     |
| `tax_rate`            |     | (Decimal) |                    -                     |           empty           | VAT amount in %                    |

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
    "req_method": "CreateSupplier",
    "req_data": {
      "name": "Supplier Name",
      "auto_shipment_load": 0,
      "country_code": "SK"
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
    "req_method": "CreateSupplier",
    "req_data": {
      "name": "Supplier Name",
      "auto_shipment_load": 0,
      "country_code": "SK",
      "delivery_days": "Delivery days",
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

## :arrow_forward: Output parameters:

| parameter       |  format   | description  |
|:----------------|:---------:|:-------------|
| `SUPPLIER_ID `  | (Integer) | Supplier ID  |

### Sample response

```json
{
  "auth_status": 201,
  "auth_status_message": "201: Auth Accepted",
  "resp_code": 401,
  "resp_note": "401: Entry Created",
  "response": {
    "SUPPLIER_ID": 4000,
    "resp_code": 401,
    "resp_note": "401: Entry Created"
  }
}
```