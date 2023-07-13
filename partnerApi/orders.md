# Get Orders

## Path
/v1/order/

## Method

GET

## Scope
orders

## Query Parameters
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| from|  | DateTime| default(null)<br />UTC | From updated (or created) date and time filter value.<br /> Example: /v1/order?from=2022-03-11T22:15:59Z |
| to|  | DateTime| default(null)<br />UTC | To updated (or created) date and time filter value.<br /> Example: /v1/order?to=2022-03-13T10:45:11Z |
| newest|  | Boolean| default(true) | If true, return in descending order newest to oldest. |
| limit|  | integer | max 1000, default(100) | Return a number of records with the set limit value. |
| offset |  | integer | default(0) | Return a subset of records starting with the offset value. |
## Success Response

HTTP Status Code: 200

Example:

```
{
    "payload": [
        {
            "orderId": "805685",
            "createdAt": "2021-01-05T00:42:54",
            "total": 172.25,
            "currency": "USD",
            "status": "Shipped Orders - PAID",
            "customerId": "592786",
            "customerNotes": "",
            "channel": "Walmart",
            "shippingMethod": "Standard Ground",
            "shippingPrice": 6.89,
            "shippingTax": 0.48,
            "shippingDiscount": 0.0,
            "handlingFee": 0.0,
            "billing": {
                "firstName": "Some",
                "lastName": "Person",
                "company": "",
                "phone": "5613765386",
                "altPhone": "",
                "fax": "",
                "zip": "33446",
                "country": "United States",
                "state": "FL",
                "city": "Delray Beach",
                "address1": "4417 Some Rd",
                "address2": "",
                "email": "someperson@relay.walmart.com"
            },
            "shipping": {
                "firstName": "Some",
                "lastName": "Person",
                "company": "",
                "phone": "5613765386",
                "altPhone": "",
                "fax": "",
                "zip": "33446",
                "country": "United States",
                "state": "FL",
                "city": "Delray Beach",
                "address1": "4417 Some Rd",
                "address2": "",
                "email": "someperson@relay.walmart.com"
            },
            "items": [
                {
                    "itemId": "2077235",
                    "productId": "3158135",
                    "unitPrice": 154.09,
                    "quantity": 1,
                    "linePosition": 1,
                    "unitWeight": 0,
                    "tax": 10.79,
                    "discount": 0.0,
                    "mpn": "834CX-3004",
                    "itemName": "Premier Sanibel Three-Handle Tub & Shower Faucet, Brushed Nickel",
                    "productImage": "https://dkstatic.blob.core.windows.net/images/561979/original/3552595_usn.jpg",
                    "productUrl": "https://www.dkhardware.com/sanibel-3-handle-1-spray-tub-and-shower-faucet-in-brushed-nickel-834cx-3004-product-3158135.html"
                }
            ]
        },
...

```

## Error Response


| HTTP status code | Message |
|--|--|
| 400 |  |
| 500 |  |
|  |  |

# Get Quotas
Looks the same as orders but different type. Instead of `orderId` is using `quoteId`

## Path
/v1/quote/

## Method

GET

## Scope
quotas

# Get Ruturns/ RMA
Looks the same as orders but different type. Instead of `orderId` is using `returnId`

## Path
/v1/return/

## Method

GET

## Scope
returns

# Get Vendor Order
Looks the same as customer orders but different type. See [Contracts](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#vendor-order)

## Path
/v1/vendor-order/

## Method

GET

## Scope
vendor-orders

# Get Vendor Quotas
Looks the same as customer quotas but different type.

## Path
/v1/vendor-quote/

## Method

GET

## Scope
vendor-quotas

# Get Vendor Ruturns/ RMA
Looks the same as customer rma but different type.

## Path
/v1/vendor-return/

## Method

GET

## Scope
vendor-returns

# Get Order by Id

## Path
/v1/order/{orderId}

## Method
GET

## Scope
orders

## Success Response
HTTP Status Code: 200
Example:

```

        {
            "orderId": "805685",
            "createdAt": "2021-01-05T00:42:54",
            "total": 172.25,
            "currency": "USD",
            "status": "Shipped Orders - PAID",
            "customerId": "592786",
            "customerNotes": "",
            "channel": "Walmart",
            "shippingMethod": "Standard Ground",
            "shippingPrice": 6.89,
            "shippingTax": 0.48,
            "shippingDiscount": 0.0,
            "handlingFee": 0.0,
            "billing": {
                "firstName": "Some",
                "lastName": "Person",
                "company": "",
                "phone": "5613765386",
                "altPhone": "",
                "fax": "",
                "zip": "33446",
                "country": "United States",
                "state": "FL",
                "city": "Delray Beach",
                "address1": "4417 Some Rd",
                "address2": "",
                "email": "someperson@relay.walmart.com"
            },
            "shipping": {
                "firstName": "Some",
                "lastName": "Person",
                "company": "",
                "phone": "5613765386",
                "altPhone": "",
                "fax": "",
                "zip": "33446",
                "country": "United States",
                "state": "FL",
                "city": "Delray Beach",
                "address1": "4417 Some Rd",
                "address2": "",
                "email": "someperson@relay.walmart.com"
            },
            "items": [
                {
                    "itemId": "2077235",
                    "productId": "3158135",
                    "unitPrice": 154.09,
                    "quantity": 1,
                    "linePosition": 1,
                    "unitWeight": 0,
                    "tax": 10.79,
                    "discount": 0.0,
                    "mpn": "834CX-3004",
                    "itemName": "Premier Sanibel Three-Handle Tub & Shower Faucet, Brushed Nickel",
                    "productImage": "https://dkstatic.blob.core.windows.net/images/561979/original/3552595_usn.jpg",
                    "productUrl": "https://www.dkhardware.com/sanibel-3-handle-1-spray-tub-and-shower-faucet-in-brushed-nickel-834cx-3004-product-3158135.html"
                }
```

## Error Response

| HTTP status code | Message |
|--|--|
| 400 |  |
| 500 |  |
|  |  |

# Get 'order-based' entities by ids
Any order-based entity can be requested in the same way as an [order by ID](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#get-order-by-id)

| Entity | Path | Scope |
|--|--|--|
| Customer Quote | /v1/quote/{quoteId} | quotas |
| Customer Order | /v1/order/{orderId} | orders |
| Customer Return /RMA | /v1/return/{returnId} | returns |
| Vendor Quote | /v1/vendor-quote/{quoteId} | vendor-quotas |
| Vendor Order | /v1/vendor-order/{orderId} | vendor-orders |
| Vendor Return /RMA | /v1/vendor-return/{returnId} | vendor-returns |

## Path
/v1/order/{orderId}

## Method
GET

## Scope
orders

# Contracts

## Common Order Fields
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| orderId | * | string | max 64 | Order identifier |
| createdAt | * | dateTime |  | Creation date and time in UTC format |
| updatedAt | * | dateTime  |  | Last changes date and time in UTC format |
| total | * | money |  | Order total |
| currency |  | string | max 10 | Currency code, default **USD** |
| status | * | string | max 100 | Order status name from **Dictionary** |
| statusId | * | string | max 10 | Order status id from **Dictionary** |
| customerId | * | string | max 64  | Customer's identifier |
| customerNotes | | string | max 8000 | Customer's notes or Cutting instructions |
| channel | | string | max 100 | Order channel name from **Dictionary**|
| shippingMethod | * | string | max 200  | Shipping method |
| shippingPrice | * | money  |  | Shipping price |
| shippingTax | * | money  |  | Shipping tax |
| shippingDiscount | | money  | default(0) | Shipping discount |
| handlingFee | | money  | default(0) | Handling fee|
| createdBy | | [User](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#user) |  | The user who created the order. |
| salesRep | | [User](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#user) |  | The user who sales representative for order. |
| vendor | | [Vendor](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#vendor) |  | The user who sales representative for order. |
| billing* | | fields from [Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#address) |  | Billing address |
| shipping* | | fields from [Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#address) |  | Shipping address |
| items | | fields from [Order Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#order-item) |  | Items |
| notes | | fields from [Note](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#note) |  | Notes |
| payments | | fields from [Payment](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#payment) | Applicable for orders and RMAs only | Payments |
| shipments | | fields from [Shipment](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#shipment) | Applicable for orders and RMAs only | Shipments |

## Order Item
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  itemId | * | string |  max 64 | Order item identifier |
| productId | * | string  | max 64 |  Product identifier|
| unitPrice | * | money |  | Product unit price |
| quantity | * | integer |  | Product quantity in order line |
| linePosition | * | integer |  | Line position |
| unitWeight |  | float |  | Product weight |
| tax |  | money   | default(0) | Total line tax |
| discount |  | money   | default(0) | Total line discount |
| mpn |  | string | max 50 | Manufacturer part number |
| itemName |  | string | max 2000 | Item name |
| productImage |  | string |  | Product main image link |
| productUrl |  | string |  | Product url for details |
| unitOfMeasure |  | [Unit Of Measure](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#unit-of-measure)|  | Product unit of measure |

## Unit Of Measure
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  id | * | string | max 10 | Unit of measure identifier |
|  name |  | string | max 50 | Unit of measure name |

## Address

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| firstName | * | string | max 150 | First name |
| lastName | * | string | max 150 | Last name |
| company |  | string | max 250 | Company name |
| phone |  | string | max 50 | Phone number |
| altPhone | | string | max 50 | Alternative phone number |
| fax |  | string |  max 50 | Fax|
| zip | * | string | max 50 | Zip/Postal code |
| country | * | string | max 150 | Country name |
| state | * | string | max 50 | State or region |
| city | * | string | max 255 | City |
| address1 | * | string  | max 255 | Address line 1 |
| address2 |  | string  | max 255 | Address line 2 |
| email |  | string  | max 100|Email address|


## Note
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| noteId | * | string  | max 64 |  Note identifier |
| message | * | string  |  max 2000 | Note message |
| actionTypeCode |  | [ActionTypeCode](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#action-type-code) |  | Code of action type |
| createdAt | * | datetime | UTC | Coordinated Universal Time of note creation |
| author |  | [User](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#user) | | The user who modified or created the note |

## Payment
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| paymentId | * | string  | max 64 |  Payment identifier |
| originalPaymentId |  | string  | max 64 |  Identifier of original payment, for example: original (charge) payment id for refund |
| amount | * | money  |  | Payment amount |
| user |  | [User](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#user) | | The user who ... |
| paymentDate | * | datetime | UTC | Coordinated Universal Time of payment |
| paymentMethod |  | [PaymentMethod](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#payment-method) |  | Payment method |
| paymentType |  | string  | 'Charge' or 'Refund' |  Type of payment |

## Payment Method
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| id | * | string | max 64 | Method identifier |
| name |  | string | max 100 | Method name |

## User
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| id | * | string | max 64 | Users's identifier |
| name |  | string | max 300 | Users's name |

## Vendor
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| id | * | string | max 64 | Vendor's identifier |
| name |  | string | max 300 | Vendors's name |

## Action Type Code

| Code | Description |
|--|--|
| WalkIn | Walk-in. |
| PhoneCall | Phone call. |
| Email | Email message. |
| Fax | Fax message. |
| General | Notes General. Most usefull type. |
| Order | Notes specific for orders. |
| QuestionToSupport | Questions/Support. |
| Cancel | Cancel Order. |

## Shipment
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| packages | | fields from [ShipmentPackage](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#shipment-package) | | Shipments packages |

## Shipment Package
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| packageId | * | string  | max 64 |  Package identifier |
| trackingNumber |  | string  | max 50 |  Tracking identifier  |
| shipDate | * | datetime |  | Date of shipment |
| carrierName |  | string  | max 50 |  Name of shipping company  |
| service |  | string  | max 250 |  Title of shipping service  |
| shippingPrice |  | money  |  | Price of shipping |

## Order
**Inherits [common order fields](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#common-order-fields)**

extra fields:

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| parentQuoteId |  | string | max 64 | Id of parent quote |
| replacementForOrderId |  | string | max 64 | Id of parent order in case of the current order is replacement |
| replacementOrderIds |  | array of string | max 64 | Replacement Ids for the current order |
| returnIds |  | array of string | max 64 | Returns Ids for the current order |

## Quote
**Inherits [common order fields](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#common-order-fields)**

extra fields:

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| orderIds |  | array of string | max 64 | Order Ids for the current quote |

## Return (RMA)
**Inherits [common order fields](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#common-order-fields)**

extra fields:

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| parentOrderId |  | string | max 64 | Id of parent order |

## Vendor Order
**Inherits [common order fields](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#common-order-fields)**

extra fields:

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| shippingType | * | string | max 50 | **Dropship** or **Coming in House** |
| parentQuoteId |  | string | max 64 | Id of parent vendor quote |
| replacementForOrderId |  | string | max 64 | Id of parent vendor order in case of the current vendor order is replacement |
| replacementOrderIds |  | array of string | max 64 | Vendor replacement order Ids for the current vendor order |
| returnIds |  | array of string | max 64 | Vendor returns Ids for the current vendor order |

## Vendor Quote
**Inherits [common order fields](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#common-order-fields)**

extra fields:

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| orderIds |  | array of string | max 64 | Vendor order Ids for the current vendor quote |

## Vendor Return (RMA)
**Inherits [common order fields](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#common-order-fields)**

extra fields:

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| parentOrderId |  | string | max 64 | Id of parent vendor order |


# Releases
-------------------------------
| Date | Version |
|--|--|
| 2022 September 12 | 20220912.1 |
### Release Notes
* Data read endpoints added.
-------------------------------
| Date | Version |
|--|--|
| 2022 October 04 | 20221004.1 |
### Release Notes
* Orders, returns, replacement orders, quotas links added.
-------------------------------
| Date | Version |
|--|--|
| 2023 April 18 | 20230418.1 |
### Release Notes
* Orders and RMAs payments added.
-------------------------------
| Date | Version |
|--|--|
| 2023 April 21 | 20230421.1 |
### Release Notes
* Orders and RMAs shipments added.
-------------------------------
