# GetShippingLabel

The method is used to obtain the shipping label for the package. If the order has multiple packages, the method returns
the label for the specified package.

## :arrow_forward: Input parameters:

Associative field with info about package.

| parameter             |                 | format        | description                                         |
|-----------------------|-----------------|---------------|-----------------------------------------------------|
| `order_id`            |                 | (Integer)     | Order ID in EGON                                    |
| `original_order_id`   |                 | (String)      | Order ID in Eshop                                   |
| `package`             |                 | (Object)      | Package object                                      |
|                       | `id`            | (Integer)     | Id in EGON                                          |
|                       | `width`         | (Integer)     | Width in mm                                         |
|                       | `height`        | (Integer)     | Height in mm                                        |
|                       | `depth`         | (Integer)     | Depth in mm                                         |
|                       | `weight`        | (Integer)     | Weight in g                                         |
| `cod`                 |                 | (Float/null)  | COD (cash on delivery) or null if it is without COD |
| `currency`            |                 | (String)      | Currency od COD                                     |
| `note`                |                 | (String/null) | Note from the order                                 |
| `customer`            |                 | (Object)      | Customer object                                     |
|                       | `company`       | (String)      | Customer company                                    |
|                       | `name`          | (String)      | Customer name                                       |
|                       | `surname`       | (String)      | Customer surname                                    |
|                       | `street`        | (String)      | Customer street                                     |
|                       | `street_number` | (String)      | Customer street number                              |
|                       | `house_number`  | (String/null) | Customer house number                               |
|                       | `city`          | (String)      | Customer city                                       |
|                       | `postal_code`   | (String)      | Customer postal code                                |
|                       | `phone`         | (String)      | Customer phone                                      |
|                       | `email`         | (String)      | Customer email                                      |
| `order_package_count` |                 | (Integer)     | Packages count in order                             |
| `order_packages`      |                 | (Array)       | Details for all packages from order                 |

### Sample request

```json
{
  "auth": {
    "auth_id": "AUTH_ID",
    "auth_key": "AUTH_KEY"
  },
  "request": {
    "req_method": "GetShippingLabel",
    "req_data": {
      "order_id": 789654,
      "order_original_id": "123456",
      "package": {
        "id": 123456,
        "width": 100,
        "height": 100,
        "depth": 100,
        "weight": 1000
      },
      "cod": 100.00,
      "currency": "CZK",
      "note": "Note from the order",
      "customer": {
        "company": "Company",
        "name": "Name",
        "surname": "Surname",
        "street": "Street",
        "street_number": "123",
        "house_number": "123",
        "city": "City",
        "postal_code": "12345",
        "phone": "+420123456789",
        "email": "email@domain.tld"
      },
      "order_package_count": 3,
      "order_packages": [
        {
          "id": 123456,
          "width": 100,
          "height": 100,
          "depth": 100,
          "weight": 1000
        },
        {
          "id": 123457,
          "width": 100,
          "height": 100,
          "depth": 100,
          "weight": 1000
        },
        {
          "id": 123458,
          "width": 100,
          "height": 100,
          "depth": 100,
          "weight": 1000
        }
      ]
    }
  }
}
```

## :arrow_forward: Output parameters:

Data obtained by decoding JSON format:

| parameter     |                | format        | description                             |
|---------------|----------------|---------------|-----------------------------------------|
| `auth_status` |                | (Integer)     | the result code of the authorization    |
| `response`    |                | (Array)       | response wrapper                        |
|               | `resp_status`  | (Integer)     | response code                           |
|               | `awb`          | (String)      | AWB from the label                      |
|               | `awb_extended` | (String)      | Barcode from the label (extended AWB)   |
|               | `base_64_pdf`  | (String)      | Label in Base64 format, PDF, 10x15 cm   |
|               | `tracking_url` | (String/null) | Tracking url for final client if exists |

:bulb: The response codes correspond to the code in
the [Response and error codes](../../code-lists/response-codes.md#--resp_status-codes)
section.

### Sample response

The sample answer in the JSON format looks like this:

```json
{
  "auth_status": 1,
  "response": {
    "resp_status": 1,
    "awb": "123456789",
    "awb_extended": "1234567890",
    "base_64_pdf": "JVBERi0xLjQKJeLjz9MKMyAwIG9iago8PC9UeXBlL0NhdGFsb2cvUGFnZXMgMiAwIFIvTGFuZ...",
    "tracking_url": "https://tracking.url.tld/123456789"
  }
}
```
