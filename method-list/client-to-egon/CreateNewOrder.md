# CreateNewOrder

The method inserts a new order into the equipment system. This method also serves to update orders if a request with an
existing original_order_id is sent to us in the system. In this case, if the order is in the state of 0,1,2,11, the
order is updated according to the newly sent data.

## Input parameters:

| parameter         | | format         | mandatory               | description                                                                       |
|----------|---|----------------|:-------------------------:|-----------------------------------------------------------------------------------|
|original_order_id | | (Integer)| :heavy_check_mark: | Order id in Your eshop / system </br>_- Order number from your eshop / system. It is a very important identificator, by which you will be able to find particular order in EGON system. In case you are creating order in EGON manually, you can choose number of your own preference._|
|business_relationship | |(String)| |Business relationship (b2b/b2c) </br>_- Based on the order designation by the Business Relationship parameter (b2b / b2c), the system monitors the settings of the goods cards "Block before expiration" or "Block before expiration for B2B" and reserves the goods for the order according to this setting._|
|reference_number | |(String)| | Reference nr of order|
|customer_name | |(String)|:heavy_check_mark:| Customer - Name |
|customer_surname | |(String)|:heavy_check_mark:| Customer - Surname |
|customer_phone | |(String)|:heavy_check_mark:| Customer - Phone |
|customer_email | |(String)|:heavy_check_mark:| Customer - Email |
|name | |(String)|:heavy_check_mark:| Delivery - Name |
|surname | |(String)|:heavy_check_mark:| Delivery - Surname |
|phone | |(String)|:heavy_check_mark:| Delivery - Phone |
|email | |(String)|:heavy_check_mark:| Delivery - Email |
|company | |(String)|:heavy_check_mark:| Delivery - Company |
|street | |(String)|:heavy_check_mark:| Delivery - Street |
|street_number | |(String)|:heavy_check_mark:| Delivery - Street number |
|entrance_number | |(String)|| Delivery - Entrance number |
|door_number | |(String)| | Delivery - Door number |
|postal_code | |(String)|:heavy_check_mark:| Delivery - ZIP code |
|city | |(String)|:heavy_check_mark:| Delivery - City|
|country | |(String)|:heavy_check_mark:| Delivery - Country |
|gps_lat | |(String)| | Latitude |
|gps_long | |(String)| | Longitude|
|fa_company | |(String)| | Billing - Company |
|fa_street | |(String)| | Billing - Street |
|fa_street_number | |(String)| | Billing - Street number |
|fa_postal_code | |(String)| | Billing - ZIP code |
|fa_city | |(String)| | Billing - City |
|fa_country | |(String)| | Billing - Country|
|fa_ico | |(String)| | Billing - ID|
|fa_dic | |(String)| | Billing - IDN|
|fa_icdph | |(String)| | Billing - VAT ID|
|invoice_url | |(String)| | Link order invoice in PDF format|
|note | |(String)|:heavy_check_mark:| Note|
|currency | |(String)| | Currency |
|default_tax | |(Integer)| | default TAX % |
|payment_card | |(Integer)| 1/0 ??? :heavy_check_mark:|- Card Payment|
|payment_cod | |(Integer)|  1/0 ??? :heavy_check_mark:| Payment - Cash on Delivery|
|cod_price_without_tax | |(Integer)| | Amount in Cash excluding VAT |
|cod_price | |(Integer)| | Amount in Cash including VAT |
|deposit_without_tax | |(Integer)| | Advance Payment excluding VAT |
|deposit | |(Integer)| | Advance including VAT |
|destination_country_code | |(String)| | Country ID |
|id_delivery | |(Integer)|:heavy_check_mark:| Transport ID |
|delivery_branch_id | |(Integer)| | Pickup point ID|
|external_branch_id | | (Integer)|?? **  | Only if delivery_branch_id is not sent, pickup point ID from an external company (e.g., Packeta)|
|delivery_price_without_tax | |(Integer)| | Shipping price excluding VAT |
|delivery_price | |(Integer)| | Shipping price including VAT |
|id_payment | |(Integer)| | ID payment|
|payment_price_without_tax | |(Integer)| | Price for payment excluding VAT |
|payment_price | |(Integer)| | Price for payment including VAT |
|discount_price_without_tax | |(Integer)| | Discount on items excluding VAT |
|discount_price | |(Integer)| | Discount on items including VAT |
|shop_setting_id | |(Integer)| | Set-to-order setting ID|
|min_delivery_date | |(String)| | Earliest delivery date (year-month) - if not completed as soon as possible|
|county | |(String)| | District of delivery address (Romania, etc.)|
|auto_process | |(Integer)| | Whether the order is to be held or processed (not a required parameter)|
|on_label | |(String)| | The name of the sender on the shipping label|
|items | |(Array)|:heavy_check_mark:| Item fields|
| | ID alebo Counter...?| | +1 stlpec :heavy_check_mark:| |
| |item_id |(Integer)| | Internal ID cards |
| |catalog_id |(String)| ???? string? nem int? |  Catalog number|
| |name |(String)| |  Product name|
| |count |(Integer)|??-pocet-Number??? |  Quantity |
| |expiration |(Integer)| ?? do description 0/1??|  Order with expiration |
| |exp_value | (String)| |  Expression in shapes \[DD-MM-YYYY, MM-YYYY, YYYY\]|
| |price |(Decimal)| |  Price excluding VAT |
| |price_with_tax |(Integer)| |  Price including VAT |
| |tax |(Integer)| |  TAX % |
|invoice | |(Array)| ?? arrray?? | Field of Invoices|
| |invoice_id |(Integer)| |  Invoice number|
| |invoice_date |(String)| |  Date of issue (Year-Month-Day)|
|fa_print | |(Integer)| | PRINT/ PRINT NOT the invoice for shipment|
|attachments | |(Array)| ??array? | Attachments to an order|



## Sample request

```json
{
  "req_method": "CreateNewOrder",
  "req_data": {
    "original_order_id": 202206015,
    "business_relationship ": "b2c",
    "reference_number ": "#EAV123",
    "customer_name": "Customer Name",
    "customer_surname": "Customer Surname",
    "customer_phone": "+421 123 567 789",
    "customer_email": "abcd@defgh.com",
    "name": "Delivery - Name",
    "surname": " Delivery - Surname",
    "phone": "+421 123 567 789",
    "email": "delivery@mail.com",
    "company": "Delivery - Company",
    "street": "Delivery - Street",
    "street_number": "Delivery - Street Number ",
    "entrance_number": "Delivery - Entrance Number",
    "door_number": "Delivery - Door Number",
    "postal_code": "Delivery - ZIP code",
    "city": "Delivery - City",
    "country": "Delivery - Country",
    "gps_lat": "48.142308",
    "gps_long": "17.100281",
    "fa_company": "Billing - Company",
    "fa_street": "Billing - Street",
    "fa_street_number": "Billing - Street Number",
    "fa_postal_code": "Billing - ZIP code",
    "fa_city": "Billing - City",
    "fa_country": "Billing - Country",
    "fa_ico": "Billing ID",
    "fa_dic": "Billing IDN",
    "fa_icdph": "Billing VAT ID",
    "invoice_url": "http://yoursite.country/invoice/123",
    "note": "Note",
    "currency": "EUR",
    "default_tax": 21,
    "payment_card": 0,
    "payment_cod": 1,
    "cod_price_without_tax": 100,
    "cod_price": 121,
    "deposit_without_tax": 10,
    "deposit": 12.1,
    "destination_country_code": "SK",
    "id_delivery": "100",
    "delivery_branch_id": 1,
    "external_branch_id": 1,
    "delivery_price_without_tax": 100,
    "delivery_price": 121,
    "id_payment": 1,
    "payment_price_without_tax": 10,
    "payment_price": 12.1,
    "discount_price_without_tax": 10,
    "discount_price": 12.1,
    "shop_setting_id": 0,
    "min_delivery_date": "2018-06-14",
    "county": "Alba",
    "auto_process": 1,
    "on_label": "MyCompany",
    "items": {
      "1": {
        "item_id": 123,
        "catalog_id": "VODA",
        "name": "Názov produktu",
        "count": 1,
        "expiration": 0,
        "exp_value": "31-12-2016",
        "price": 49.59,
        "price_with_tax": 60,
        "tax": 21
      }
    },
    "invoice": {
      "invoice_id": 123,
      "invoice_date": "31-12-2016"
    },
    "fa_print": 1,
    "attachments": [
      "http:\\\/\\\/yoursite.country\\\/\\\/export\\\/docs\\\/orderAttachment1.pdf",
      "http:\\\/\\\/yoursite.country\\\/\\\/export\\\/docs\\\/orderAttachment2.pdf"
    ]
  }
}  

```

## Output parameters:

| parameter       |                       | format      | description                           |
|-----------------|-----------------------|-------------|---------------------------------------|
| `resp_code`     |                       | (Integer)   |                 |
| `resp_message`  |                       | (String)    |                 |
| `resp_data`     |                       | (Integer)   |                 |
|                 | `order_id`            | (Integer)   |                 |

## Sample response

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
      "order_id": 6205572
    }
  }
}
```