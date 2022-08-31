# Contracts
## Product
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  productId | * | string | max 64 | Product identifier |
|  productCode |  | string | max 50 | Product code for internal usage. General same as MPN |
| mpn |  | string | max 50 | Manufacturer part number |
| upc |  | string | max 50 | UPC or GTIN |
| name |  | string | max 2000 | Product name |
| fullName |  | string | max 2000 | Brand + MPN + name |
| description |  | string |  | Product description |
| mainImage |  | string |  | Product main image link |
| url |  | string |  | Product url for details |
| brand |  | [Brand](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/products.md#brand) |  | Product brand |
| manufacturer |  | [Manufacturer](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/products.md#manufacturer) |  | Product manufacturer |
| discontinued |  | Boolean |  | Product is discontinued |
| hold |  | Boolean |  | Product has put on hold |
| hidden |  | Boolean |  | Product is hidden on web site |
| system |  | Boolean |  | Product is system (for example coupons) |
| freightOnly |  | Boolean |  | Can be shipped only by ground by tracks |
| mustCut |  | Boolean |  | Is long item, need cutting instruction |
| oversize |  | Boolean |  | Product is oversize |
| oversizeType |  | Integer | 1..5 | Oversize type |
| size |  | string | max 50 | Product size (is using in varitions) |
| finish |  | string | max 255 | Product finish or color (is using in varitions) |
| packSize |  | Integer |  | pack size (is using in varitions) |


## Brand
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  brandId | * | string | max 64 | Brand identifier |
|  name | * | string | max 100 | Brand name |

## Manufacturer
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  manufacturerId | * | string | max 64 | Manufacturer identifier |
|  name | * | string | max 100 | Manufacturer name |
