<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/images/logo_white.png">
  <img alt="logo" src="assets/images/logo_black.png">
</picture>

# Documentation for the RestAPI v1 client

The API Client Web Service ("API") is intended for [isklad.eu](https://isklad.eu) clients who need to transfer data
between their information
system (e-commerce) and isklad.eu's information system via this service.

The API is implemented on isklad.eu and is accessible via the Internet. Provides a set of methods for exchanging storage
card data, orders, shipping methods, payments, invoices, etc ...

The isklad.eu project is constantly developing and the set of methods is being continuously complemented by other new
services. For this reason, the most up-to-date version of this documentation, which is provided by your isklad.eu
merchant, is necessary to implement.

The documentation contains a detailed description of each available method with the following details:

- Description of input parameters and their values
- Example request
- Sample Response

## Table of contents:

- **Integration manuals**
  - [Client-> EGON](integration/client-to-egon.md)
  - [EGON-> Client](integration/egon-to-client.md)
  
- **Method list Client -> EGON**
  - UpdateInventoryCard
  - CreateNewOrder
  - StornoOrder
  - GetOrderStatus
  - InventoryDetail
  - CreatePackage
  - TrackPackage
  - GetOrderInventoryExpiration
  - ShippingOptions
  - PackingOptions
  - CreateEshopSettings
  - CreateSupplier
  - ShipmentNotify
  - InventoryCardExpiration
  - CreateOrderReturnLabel
  
- **Method list EGON -> Client**
  - WriteOrderStatus
  - GetInvoiceUrl
  - InventoryStatusUpdate
  - UpdatePackageTracking
  - ShipmentNotifyConfirm
  
- **Code lists**
  - [Response and error codes](code-lists/response-codes.md)
  - [Country list](code-lists/country-list.md)
  - [Order status list](code-lists/order-statuses.md)
  - [Transport type list](code-lists/transport-type-list.md)
  - [Payment method list](code-lists/payment-method-list.md)
  - [Package tracking code list](code-lists/package-tracking-codes.md)
