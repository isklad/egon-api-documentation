<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/images/logo_white.png">
  <img alt="logo" src="assets/images/logo_black.png">
</picture>

# Documentation for the EGON RestAPI v1 client

The API Client Web Service is intended for [isklad.eu](https://isklad.eu) clients who need to transfer data
between their information system (e-commerce) and isklad.eu's information system (called **EGON**) via this service.

The API is implemented on isklad.eu and is accessible via the Internet. Provides a set of methods for exchanging storage
card data, orders, shipping methods, payments, invoices, etc ...

The documentation contains a detailed description of each available method with the following details:

- Description of input parameters and their values
- Sample request
- Description of output parameters and their values
- Sample Response

The isklad.eu project is constantly developing and the set of methods is being continuously complemented by other new
services. For this reason, the most up-to-date version of this documentation, which is provided by your isklad.eu
merchant, is necessary to implement.

## Subscribe for future changes ![recommended](assets/images/recommended.png)
Please subscribe :eyes: :thumbsup: to this repository and stay informed about our future changes.
See more at [Managing subscriptions and notifications on GitHub](https://docs.github.com/en/account-and-profile/managing-subscriptions-and-notifications-on-github)


## Table of contents:

- **Integration manuals**
  - [Client-> EGON](integration/client-to-egon.md)
  - [EGON-> Client](integration/egon-to-client.md)
  
- **Method list Client -> EGON**
  - [CreateEshopSetting](method-list/client-to-egon/CreateEshopSetting.md)
  - [CreateNewOrder](method-list/client-to-egon/CreateNewOrder.md)
  - [CreateOrderReturnLabel](method-list/client-to-egon/CreateOrderReturnLabel.md)
  - [CreatePackage](method-list/client-to-egon/CreatePackage.md)
  - [CreateSupplier](method-list/client-to-egon/CreateSupplier.md)
  - [GetOrderInventoryExpiration](method-list/client-to-egon/GetOrderInventoryExpiration.md)
  - [GetOrderStatus](method-list/client-to-egon/GetOrderStatus.md)
  - [InventoryCardExpiration](method-list/client-to-egon/InventoryCardExpiration.md)
  - [InventoryDetail](method-list/client-to-egon/InventoryDetail.md)
  - [PackingOptions](method-list/client-to-egon/PackingOptions.md)
  - [ShipmentNotify](method-list/client-to-egon/ShipmentNotify.md)
  - [ShippingOptions](method-list/client-to-egon/ShippingOptions.md)
  - [StornoOrder](method-list/client-to-egon/StornoOrder.md)
  - [TrackPackage](method-list/client-to-egon/TrackPackage.md)
  - [UpdateInventoryCard](method-list/client-to-egon/UpdateInventoryCard.md)
  
- **Method list EGON -> Client**
  - [GetInvoiceUrl](method-list/egon-to-client/GetInvoiceUrl.md)
  - [InventoryStatusUpdate](method-list/egon-to-client/InventoryStatusUpdate.md)
  - [OrderReturnLabelTracking](method-list/egon-to-client/OrderReturnLabelTracking.md)
  - [ShipmentNotifyConfirm](method-list/egon-to-client/ShipmentNotifyConfirm.md)
  - [UpdatePackageTracking](method-list/egon-to-client/UpdatePackageTracking.md)
  - [WriteOrderStatus](method-list/egon-to-client/WriteOrderStatus.md)
  - [MyOrderClaimUpdate](method-list/egon-to-client/MyOrderClaimUpdate.md)

- **Code lists**
  - [Response and error codes](code-lists/response-codes.md)
  - [Country list](code-lists/country-list.md)
  - [Order status list](code-lists/order-statuses.md)
  - [Package tracking code list](code-lists/package-tracking-codes.md)
  - [Payment method list](code-lists/payment-method-list.md)
  - [Transport type list](code-lists/transport-type-list.md)
