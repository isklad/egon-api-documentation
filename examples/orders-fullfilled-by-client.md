# Create a shipment/label
Shipment/label order is an order that is not fulfilled by iSklad. 
The client is responsible for the fulfillment process and isklad only provides shipping label.

## :arrow_forward: Minimal sample request:
- NOTE: showing only `request` request part
### Create order/shipment - [CreateNewOrder](../method-list/client-to-egon/CreateNewOrder.md)
```json
{
  "req_method": "CreateNewOrder",
  "req_data": {
    "order_type": "external",
    "original_order_id": 202206015,
    "shop_setting_id": 1,
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
    "city": "Delivery - City",
    "country": "Delivery country code, e.g.: SK",
    "postal_code": "Delivery - ZIP code",
    "destination_country_code": "SK",
    "id_delivery": 1,
    "payment_cod": 0,
    "items": [],
    "packages": [
      {
        "weight": 500
      }
    ]
  }
}
```

## :arrow_forward: Advanced ![recommended](../assets/images/recommended.png) sample request:
- NOTE: showing only `request` request part

### Create a supplier - [CreateSupplier](../method-list/client-to-egon/CreateSupplier.md) - with details of your inventory card
- your supplier data is needed for some delivery companies (e.g. for customs), so it is recommended to create it
```json
{
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
```
### Create an inventory card - [UpdateInventoryCard](../method-list/client-to-egon/UpdateInventoryCard.md) - with details for your order
- inventory data i needed for some delivery companies (e.g. for customs), so it is recommended to create it
- for customs - needed params: weight, commodity code, declaration description, etc.
- is recommended to fill all the fields, you have in your system
```json
{
  "req_method": "UpdateInventoryCard",
  "req_data": {
    "item_id": 123456,
    "shop_setting_id": 1,
    "catalog_id": "A1A",
    "parent_catalog_id": "A1",
    "name": "product name",
    "mj": "pcs",
    "ean": "123456789012",
    "enabled": 1,
    "category": [
      "category name"
    ],
    "producer": "my producer",
    "price_without_tax": 1.25,
    "old_price_without_tax": 1.55,
    "tax": 20,
    "supplier": "my main supplier",
    "short_description": "product description",
    "long_description": "long product description",
    "min_order_count": 1,
    "tech_char": {
      "param_1": "param value"
    },
    "tech_param": {
      "param_1": "param value"
    },
    "images": [
      {
        "url": "https://domain.tld/img1.jpg",
        "order": 1,
        "enabled": 1
      }
    ],
    "is_electronic_product": 0,
    "commodity_code": null,
    "declaration_description": null,
    "weight_grams": 100
  }
}
```
### Create an order/shipment - [CreateNewOrder](../method-list/client-to-egon/CreateNewOrder.md)
- contains all the details of the order, including items, delivery, payment, etc.
- for customs - the invoice data is also needed
- is recommended to fill all the fields, you have in your system
```json
{
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
    "city": "Delivery - City",
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
    "on_label": "MyCompany",
    "note": "Note",
    "currency": "EUR",
    "destination_country_code": "SK",
    "id_delivery": "Transport ID",
    "default_tax": 21,
    "id_payment": 1,
    "payment_cod": 0,
    "cod_price": 121,
    "deposit": 12.1,
    "delivery_price": 121,
    "payment_price": 12.1,
    "discount_price": 12.1,
    "items": [
      {
        "item_id": 123,
        "catalog_id": "Water",
        "name": "Product name",
        "count": 1,
        "expiration": 0,
        "exp_value": "2022-08-01",
        "price_with_tax": 60,
        "tax": 21
      }
    ],
    "invoice": {
      "invoice_id": 123,
      "invoice_date": "2022-08-01"
    },
    "invoice_url": "https://domain.tld/invoice/123",
    "packages": [
      {
        "weight": 500
      }
    ]
  }
}
```
### Get the final order details - [GetOrderStatus](../method-list/client-to-egon/GetOrderStatus.md)
- contains all the details of the order, including the delivery labels
- you can find the created labels in the response under `packages/label`
```json
{
  "req_method": "GetOrderStatus",
  "req_data": {
    "order_id": 132321
  }
}
```
