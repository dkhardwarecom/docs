## Order
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  orderId | * | integer |  | Order identifier |
| createdAt | * | dateTime |  | Creation date and time in UTC format |
| updatedAt | * | dateTime  |  | Last changes date and time in UTC format |
| total | * | money |  | Order total |
| currency |  | string | max 10 | Currency code, default **USD** |
| status | * | string | max 100 | Order status name from **Dictionary** |
| customerId | * | integer |  | Customer's identifier |
| customerNotes | | string | max 8000 | Customer's notes or Cutting instructions |
| channel | | string | max 100 | Order channel name from **Dictionary**|
| shippingMethod | * | string | max 200  | Shipping method |
| shippingPrice | * | money  |  | Shipping price |
| shippingTax | * | money  |  | Shipping tax |
| shippingDiscount | | money  | default(0) | Shipping discount |
| handlingFee | | money  | default(0) | Handling fee|
| billing* | | fields from [Address](https://dkhardware.visualstudio.com/DkHardware/_wiki/wikis/DkHardware.wiki/403/Orders?anchor=address) |  | Billing address |
| shipping* | | fields from [Address](https://dkhardware.visualstudio.com/DkHardware/_wiki/wikis/DkHardware.wiki/403/Orders?anchor=address) |  | Shipping address |

## Order Item
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  itemId | * | integer |  | Order item identifier |
|  orderId | * | integer |  | Order identifier |
| productId | * | integer  |  |  Product identifier|
| unitPrice | * | money |  | Product unit price |
| quantity | * | integer |  | Product quantity in order line |
| linePosition | * | integer |  | Line position |
| lineComment |  | integer |  | Additional line comment |
| unitWeight |  | float |  | Product weight |
| tax |  | money   | default(0) | Total line tax |
| discount |  | money   | default(0) | Total line discount |
| mpn |  | string | max 50 | Manufacturer part number |
| productTitle |  | string | max 2000 | Product title |
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
