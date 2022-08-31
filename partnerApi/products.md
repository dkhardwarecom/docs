# Contracts
## Product
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  productId | * | string | max 64 | Product identifier |
|  productCode |  | string | max 50 | Product code for internal usage. General same as MPN |
| mpn |  | string | max 50 | Manufacturer part number |
| name |  | string | max 2000 | Product name |
| fullName |  | string | max 2000 | Brand + MPN + name |
| mainImage |  | string |  | Product main image link |
| url |  | string |  | Product url for details |
| brand |  | [Brand](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/products.md#brand) |  | Product brand |
| manufacturer |  | [Manufacturer](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/products.md#manufacturer) |  | Product manufacturer |

## Brand
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  brandId | * | string | max 64 | Brand identifier |
|  name | * | string | max 100 | Brand name |

## Manufacturer
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  manufacturerId | * | string | max 64 | Brand identifier |
|  name | * | string | max 100 | Brand name |
