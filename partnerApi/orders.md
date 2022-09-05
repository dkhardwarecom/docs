# Get Orders

## Path
/v1/order/

## Method

GET

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
                "firstName": "Gloria",
                "lastName": "Thompson",
                "company": "",
                "phone": "5613765386",
                "altPhone": "",
                "fax": "",
                "zip": "33446",
                "country": "United States",
                "state": "FL",
                "city": "Delray Beach",
                "address1": "8602 Sawpine Rd",
                "address2": "",
                "email": "D37B99CFACAC4DF691193B0441108F86@relay.walmart.com"
            },
            "shipping": {
                "firstName": "Gloria",
                "lastName": "Thompson",
                "company": "",
                "phone": "5613765386",
                "altPhone": "",
                "fax": "",
                "zip": "33446",
                "country": "United States",
                "state": "FL",
                "city": "Delray Beach",
                "address1": "8602 Sawpine Rd",
                "address2": "",
                "email": "D37B99CFACAC4DF691193B0441108F86@relay.walmart.com"
            },
            "items": [
                {
                    "itemId": "2077235",
                    "productId": "3158135",
                    "unitPrice": 154.09,
                    "quantity": 1,
                    "linePosition": 1,
                    "lineComment": "",
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

# Get Quotes
Looks the same as orders but different type. Instead of `orderId` is using `quoteId`

## Path
/v1/quote/

## Method

GET

# Get Ruturns/ RMA
Looks the same as orders but different type. Instead of `orderId` is using `returnId`

## Path
/v1/return/

## Method

GET

# Get Vendor Order
Looks the same as customer orders but different type.

## Path
/v1/vendor-order/

## Method

GET

# Get Vendor Quotes
Looks the same as customer quotes but different type.

## Path
/v1/vendor-quote/

## Method

GET

# Get Vendor Ruturns/ RMA
Looks the same as customer rma but different type.

## Path
/v1/vendor-return/

## Method

GET

# Contracts

## Order
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  orderId | * | string | max 64 | Order identifier |
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
| billing* | | fields from [Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#address) |  | Billing address |
| shipping* | | fields from [Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#address) |  | Shipping address |

## Order Item
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  itemId | * | string |  max 64 | Order item identifier |
| productId | * | string  | max 64 |  Product identifier|
| unitPrice | * | money |  | Product unit price |
| quantity | * | integer |  | Product quantity in order line |
| linePosition | * | integer |  | Line position |
| lineComment |  | integer |  | Additional line comment |
| unitWeight |  | float |  | Product weight |
| tax |  | money   | default(0) | Total line tax |
| discount |  | money   | default(0) | Total line discount |
| mpn |  | string | max 50 | Manufacturer part number |
| itemName |  | string | max 2000 | Item name |
| productImage |  | string |  | Product main image link |
| productUrl |  | string |  | Product url for details |

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
