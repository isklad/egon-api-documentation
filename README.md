<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/images/logo_white.png">
  <img alt="logo" src="assets/images/logo_black.png">
</picture>

# Documentation for the EGON RestAPI v1 client

The API Client Web Service is intended for [isklad.com](https://isklad.com) clients who need to transfer data
between their information system (e-commerce) and isklad.com's information system (called **EGON**) via this service.

The API is implemented on isklad.com and is accessible via the Internet. Provides a set of methods for exchanging storage
card data, orders, shipping methods, payments, invoices, etc ...

The documentation contains a detailed description of each available method with the following details:

- Description of input parameters and their values
- Sample request
- Description of output parameters and their values
- Sample Response

The isklad.com project is constantly developing and the set of methods is being continuously complemented by other new
services. For this reason, the most up-to-date version of this documentation, which is provided by your isklad.com
merchant, is necessary to implement.

## Subscribe for future changes ![recommended](assets/images/recommended.png)
Please subscribe :eyes: :thumbsup: to this repository and stay informed about our future changes.
See more at [Managing subscriptions and notifications on GitHub](https://docs.github.com/en/account-and-profile/managing-subscriptions-and-notifications-on-github)


## Table of contents:

- **Examples**
  - [Create a regular order](examples/orders-fulfilled-by-isklad.md) - if the fulfillment process is **managed by iSklad**
  - [Create a shipment/label](examples/orders-fullfilled-by-client.md) - if the fulfillment process is **managed by an external company, or client himself**
- **Integration manuals**
  - [Client-> EGON](integration/client-to-egon.md)
  - [EGON-> Client](integration/egon-to-client.md)
  
- **Method list Client -> EGON**
  - [CreateEshopSetting](method-list/client-to-egon/CreateEshopSetting.md)
  - [CreateNewOrder](method-list/client-to-egon/CreateNewOrder.md)
  - [CreateOrderReturnLabel](method-list/client-to-egon/CreateOrderReturnLabel.md) ![deprecated](/assets/images/deprecated.png)
  - [CreateProducer](method-list/client-to-egon/CreateProducer.md)
  - [CreateSupplier](method-list/client-to-egon/CreateSupplier.md)
  - [GetOrderInventoryExpiration](method-list/client-to-egon/GetOrderInventoryExpiration.md)
  - [GetOrderStatus](method-list/client-to-egon/GetOrderStatus.md)
  - [InventoryCardExpiration](method-list/client-to-egon/InventoryCardExpiration.md)
  - [InventoryDetail](method-list/client-to-egon/InventoryDetail.md)
  - [PackingOptions](method-list/client-to-egon/PackingOptions.md)
  - [ShipmentNotify](method-list/client-to-egon/ShipmentNotify.md)
  - [ShippingOptions](method-list/client-to-egon/ShippingOptions.md)
  - [StornoOrder](method-list/client-to-egon/StornoOrder.md)
  - [TrackPackage](method-list/client-to-egon/TrackPackage.md) ![deprecated](/assets/images/deprecated.png)
  - [UpdateInventoryCard](method-list/client-to-egon/UpdateInventoryCard.md)
  - [ChangeClaimStatus](method-list/client-to-egon/ChangeClaimStatus.md)
  - [StockMovements](method-list/client-to-egon/StockMovements.md)
  - [CreateMyOrderOTP](method-list/client-to-egon/CreateMyOrderOTP.md)
  
- **Method list EGON -> Client**
  - [GetInvoiceUrl](method-list/egon-to-client/GetInvoiceUrl.md)
  - [InventoryStatusUpdate](method-list/egon-to-client/InventoryStatusUpdate.md)
  - [OrderReturnLabelTracking](method-list/egon-to-client/OrderReturnLabelTracking.md)
  - [ShipmentNotifyConfirm](method-list/egon-to-client/ShipmentNotifyConfirm.md)
  - [UpdatePackageTracking](method-list/egon-to-client/UpdatePackageTracking.md) ![deprecated](/assets/images/deprecated.png)
  - [WriteOrderStatus](method-list/egon-to-client/WriteOrderStatus.md)
  - [MyOrderClaimUpdate](method-list/egon-to-client/MyOrderClaimUpdate.md)
  - [GetShippingLabel](method-list/egon-to-client/GetShippingLabel.md)

- **Code lists**
  - [Response and error codes](code-lists/response-codes.md)
  - [Country list](code-lists/country-list.md)
  - [Order status list](code-lists/order-statuses.md)
  - [Package tracking code list](code-lists/package-tracking-codes.md)
  - [Payment method list](code-lists/payment-method-list.md)
  - [Transport type list](code-lists/transport-type-list.md)

